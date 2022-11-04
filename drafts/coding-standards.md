# Some Coding Standards

## Format

- please install prettier, and use the configured prettier format (editor plugins could run this on save, please enable so in your respective editors

## Variable declarations
- use `const` as much as possible, only use `let` for special ocasions, never use `var`

## Naming conventions
- nouns for varianbles, verbs for functions, and both in `camelCase`
- classes and namespaces should be in `PascalCase`
- functions and methods should be a verb in `camelCase`
- parameters should use `camelCase` i.e. `function getZ( width, someHeight ){}`
- constants should be in `UPPER_SNAKE_CASE` (note that using `consts` could also mean an immutable varialbe, immutable variables should still be in `camelCase`, usage of `const` does not always mean a "CONSTANT", by constant, we mean something like a config, setting, hard-coded values, and other things along those lines)
- filenames are in `small-kebab-case` (unless frameworks used dictate otherwise)
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
## Equality
- always prefer strict checks `===` and `!==`, do not use `==` and `!=`

## Use the `for` construct sparingly
- the `for` construct is more performant but most of the time, using `map` and or `forEach` (even `reduce`) is more readable.

## Respect the linter

## Prefer the `async/await` construct
- when possible, use `async/await`, usage priority is as follows `async/await` > `promises` > `callbacks`, from most preferred to less preferred.

## Comments
- comments should mostly contain the "why the code" and not the "what the code does", we can identify the "what the code does" by reading the code, the "why", not so much, so please prefer to add comments that answers the "whys"

## Prefer guard-clauses, aka early returns
instead of
```js
function isOpen(ticket) {
  if (ticket.status === "Open") {
    return true
  } else {
    if (ticket.isActive === true) {
      return true
    } else {
      return false
    }
  }
}
```
prefer
```js
function isOpen(ticket) {
  if (ticket.status === "Open") {
    return true
  }
  if (ticket.isActive) {
    return true
  }
  return false
}
```

## prefer (single-labeled) obj params as Function parameters
aside, please be aware of the correct usage of the term "parameter" and "argument", for below example
```js
function computeBMI1( height, weight ) {
  // some calculations
}

computeBMI1(160, 70)
```
`height` and `weight` are the parameters, whereas `160` and `70` are the arguments.
with that out of the way, please prefer using single complex labeled types like below
```js
function computeBMI2( { height, weight } ) {
  // some calculations
}

computeBMI2({ height: 160, weight: 70})
```
notice that the `computeBMI2` variant is more readable than the `computeBMI1` one.
"single" param is not a hard rule, we could use multiple labeled obj params for complex params/functions if needed, always group related params to a single obj

## other `function` constructs
for more function related stuff (read on function composition -`compose` & `pipe`, currying, and other constructs we can leverage from having closures and first-class function support)

## lets reserve the prefix `make` for HOFs 
- higher-order functions, similar to React's more popular higher-order-components (HOCs)
- higher-order functions are functions that return another function when called.
example
```js
function makePrinterWithLabelHOF(label) {
  return function(text) {
    console.log(`${label}: ${text}`)
  }
}
const printWithRedLabel= makePrinterWithLabelHOF("red")
printWithRedLabel('hey') // red: hey

// or simply
const makePrinterWithLabelHOF2 = label => text => console.log(`${label}: ${text}`)
```
