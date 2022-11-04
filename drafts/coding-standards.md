# Format

- please install prettier, and use the configured prettier format (editor plugins could run this on save, please enable so in your respective editors

# Variable declarations
- use `const` as much as possible, only use `let` for special ocasions, never use `var`

# Naming conventions
- nouns for varianbles, verbs for functions
- classes and namespaces should be in `PascalCase`
- functions and methods should be a verb in `camelCase`
- constants should be in `UPPER_SNAKE_CASE`
- filenames are in `small-kebab-case` (unless frameworks used dictates otherwise)
- please add jsdoc as much as possible (see more https://jsdoc.app)
```js
// below is a sampol jsdoc comment notice the double (**) after / above

/**
* An example function that does nothing
* @returns {Number} Returns 0
*/
function example() { return 0 }

/** This is a description of the example2 function. */
function example2() {}
```
# Equality
- always prefer strict checks `===` and `!==`, do not use `==` and `!=`

# Use the `for` construct sparingly
- the `for` construct is more performant but most of the time, using `map` and or `forEach` (even `reduce`) is more readable.

# Respect the linter

# Prefer the `async/await` construct
- when possible, use `async/await`, usage priority is as follows `async/await` > `promises` > `callbacks`, from most preferred to less preferred.

# Comments
- comments should mostly contain the "why the code" and not the "what the code does", we can identify the "what the code does" by reading the code, the "why", not so much, so please prefer to add comments that answers the "whys" 
