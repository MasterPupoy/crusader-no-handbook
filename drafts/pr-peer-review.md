## forever draft na guidelines sa pag peer review

1. ongoing feedback and communication is encouraged.
We want to foster a culture of open communication and continuous feedback. Members are encouraged to ask questions, clarify misunderstandings, and discuss concerns in real-time, rather than waiting for formal code review.
1. PRs should only do 1 boring thing please, make them as small as possible, no mixing of features, fixes, and refactors please
1. Descriptions, use imperative business language descriptions please, answer the question "What happens when the PR is merged", will `Feat: add button to block a user`
1. time-boxed reviews, reviews should only take less than 20 mins, 30mins tops, ideal is even less than 5mins
1. Reviews that could be taken as a follow up tickets should be preferred, prioritize merging PR and prefer the "fix-later-in-a-new-PR" approach as much as possible
1. Fix them warnings

## General Guidelines:

1. Review the code, not the person: Focus on the code changes and avoid personal remarks. Be respectful and professional in your feedback.
1. Be concise and clear: Provide clear and actionable feedback. Avoid vague comments and instead, point out specific lines of code or suggestions for improvement.
1. Encourage best practices: Encourage the use of best practices, design patterns, and idiomatic code for your stack.

## TypeScript:

1. Type safety: Ensure that the code uses appropriate types and interfaces to catch potential issues at compile-time.
1. Proper use of type guards and type assertions: Check that type guards and type assertions are used correctly and only when necessary.
1. Prefer use of `unknown` over `any`

## React:

1. Component structure: Ensure that components are well-structured, modular, and reusable. Avoid overly complex or monolithic components. Components should ideally do one(1) single boring thing, like layout only, retrieval only, data display only.
1. State management: Check that state management is done appropriately using useState, useReducer, etc. Ideal would be all states are contained in our URLs
1. Use of hooks: Verify that hooks are used correctly, and custom hooks are created when needed for better code organization.
1. Performance optimization: Check that the code leverages useMemo, useCallback, and React.memo to optimize performance where necessary.

## Node.js:

1. Proper error handling: Ensure that errors are handled correctly, and appropriate error messages are propagated back to the client. Only use try-catch for `exceptional` cases, when we are unable to predict the result, for the rest, please perfer the `ResultType` pattern, internally known as `TOkayable`

## GraphQL:

1. Schema design: Ensure that the GraphQL schema is well-designed, with clear types, queries, and mutations. Ideally, queries and mutations should do 1 single boring thing.
1. Resolvers: Verify that resolvers are efficient, and any necessary batching or caching is implemented. Avoid using `db`/`prisma` directly, please refer to `data-services` as much as possible.

## Prisma:

1. Proper use of Prisma Client: Check that the Prisma Client is used correctly to interact with the database and that queries are efficient. Please prefer using `db.$transaction` for multiple related data changes.
1. Schema design: Ensure that the Prisma schema is well-designed and follows best practices for your data model. Please seek approval for these types of changes

## Tailwind CSS:

1. Proper use of utility classes: Verify that the code uses utility classes correctly and avoids unnecessary duplication or overrides.
1. Responsive design: Check that the design is responsive and works well on different devices and screen sizes. Mobile first
1. Prefer usage of themed colors/variable, like instead of `green`, we use `btn-success` or something.

## Automated testing:

1. Test coverage: Ensure that the code changes include appropriate test coverage (unit, integration, and end-to-end tests).
1. Test quality: Verify that tests are well-written, readable, and maintainable.

## Code quality and maintainability:

1. Readability: Check that the code is easy to read, understand, and maintain.
1. Consistent code style: Ensure that the code follows a consistent style, such as using the Prettier formatter and adhering to the team's style guide.
1. Comments and documentation: Verify that the code includes clear comments and documentation where necessary.

## Refactors
- refactors should NEVER update a test case/snapshot. A change in test or snapshot mean a change in function, change in function is not a refactor, it should be a fix or a feat.
