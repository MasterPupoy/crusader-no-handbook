# Page Object Model (POM)
1. Page components abstraction: Create separate components (or factory functions) for different sections or elements of your web application. Each component should contain the methods required to interact with those specific elements. In the example above, we created a LoginPage component with methods to set the username, set the password, click the login button, and get the error message.
1. Encapsulate selectors and actions: Encapsulate the CSS selectors and actions within the page components. This helps keep your test code clean, readable, and maintainable. If the structure of your web application changes, you only need to update the relevant page component instead of updating each test.
1. Keep your tests focused on the scenarios: With the POM pattern in place, your tests should focus on the scenarios you want to validate, rather than the details of interacting with the page. This means you can write tests that are more understandable, maintainable, and resistant to changes in the application's structure.
1. Reuse components: The POM pattern allows you to reuse components across multiple test suites. If you have several test suites that need to interact with the same page or section of your application, you can easily reuse the existing page components.


## Sampols

### Sampol POM

```typescript
// LoginPage.ts
import { Page } from 'playwright';

interface LoginPage {
  navigate: () => Promise<void>;
  setUsername: (username: string) => Promise<void>;
  setPassword: (password: string) => Promise<void>;
  clickLoginButton: () => Promise<void>;
  getErrorMessage: () => Promise<string>;
}

export function createLoginPage(page: Page, baseUrl: string): LoginPage {
  const url = `${baseUrl}/login`;

  return {
    async navigate() {
      await page.goto(url);
    },

    async setUsername(username: string) {
      await page.fill('#username', username);
    },

    async setPassword(password: string) {
      await page.fill('#password', password);
    },

    async clickLoginButton() {
      await page.click('#login-button');
    },

    async getErrorMessage() {
      return await page.textContent('#error-message');
    },
  };
}
```


### How to use

```typescript
// tests/login.spec.ts
import { test, expect } from '@playwright/test';
import { createLoginPage } from '../LoginPage';

test.describe('Login Tests', () => {
  let loginPage;

  test.beforeEach(async ({ page }) => {
    const baseUrl = 'https://your-website.com';
    loginPage = createLoginPage(page, baseUrl);
    await loginPage.navigate();
  });

  test('Valid login', async ({ page }) => {
    await loginPage.setUsername('validUsername');
    await loginPage.setPassword('validPassword');
    await loginPage.clickLoginButton();
    await expect(page).toHaveURL('https://your-website.com/dashboard');
  });

  test('Invalid login', async () => {
    await loginPage.setUsername('invalidUsername');
    await loginPage.setPassword('invalidPassword');
    await loginPage.clickLoginButton();
    const errorMessage = await loginPage.getErrorMessage();
    expect(errorMessage).toEqual('Invalid username or password');
  });
});
```
