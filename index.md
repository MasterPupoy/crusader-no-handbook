# Index

## The `ResultType` (infamously known as `TOkayable`)
`methodThatCouldError() : {ok: true, data: any} | {ok: false, error: any}` <- this signature is king

## Switch Case (Exhaustive Checking)
https://www.typescriptlang.org/docs/handbook/2/narrowing.html#exhaustiveness-checking

## Discriminated Unions
this is not a "ts only" concept, but linking below ts docu because it is whats relevant for us.
https://www.typescriptlang.org/docs/handbook/2/narrowing.html#discriminated-unions

## Avoid the `if([])` trap
Empty array in javascript is considered `true` (truthy). So instead of using `if(someArray){}`, please use `if(someArray.length > 0)`
