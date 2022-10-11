#### make components as dumb as possible
yes we have dumb and smart components, in-cases where components are smart, please lets not make them "too" smart, be dumb as dumb as possible.
##### why
- for ease of testing and replication
- easier to understand with fewer movable parts involved
##### ways to restrict smartness
- restrict importing anything, pass as props as much as possible, imports should be in page components
- dont use "globals", like "window", or libs that returns global values

#### law of demeter
#### limit scope to the smallest range as small as possible
- no globals
- smallest lexical scope
- see closures
#### you don't need to create something most of the time, ask a provider (DI)
#### immutables
#### purity 
#### prefer to style the surroundings of a (reusable) component when used/called, leave the components "main" wrapper unstyled
- we do this to have flexibility when reusing components

##### what i mean is

```ts
// this should be avoided
const Component = () => {
  ...
  return <Box styling> // <-- this should be avoided, prefer an empty unstyled frag or unstyled container
   // ...contents 
  </Box>
}

const ParentPageOrSumthin = () => {
  return <Component />
}
```
do it this instead

```ts

const Component = () => {
  ...
  // notice the lack of styling of the "wrapping fragment", we moved the "Box" of above to the calling component, see below
  return <> ...contents </>
}

const ParentPageOrSumthin = () => {
  return <Box addstyleshere> // <-- we moved the box here 
     <Component />
  </Box>
}
```
- further reading, https://mxstbr.com/thoughts/margin/ https://dev.to/seya/how-to-style-margin-with-react-8m9 altho articles mostly mention "margins", this also apply to most of other "layoutee" styles

#### https://github.com/ftmobsquad/mdt-yougou/issues/1172

#### do not branch to get away from errors, let it fail and handle in the caller
avoid isolated `if` statements, isolated `if`s are those with no `else` pairs, instead of creating `if` clauses, or instead of introducing new expressions inside existing `if`s, prefer to let it fail but add proper handling somewhere the calltree (like with `try-catch` or with the `ResultType`),
addition of `expressions/if` introduces more "silent failing unhandlelable scenarios" which we do not want in our system. Prefer to Fail early, then handle exceptions properly.
