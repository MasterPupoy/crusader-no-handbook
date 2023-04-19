# Changesets

## What to write as body?

Please write a brief description of the change, high level, no need to specify the filename unless you think super necessary, after the description, please include the answer to "Why the change?", some common answer to the why includes, fix a broken feature, and/or to enable a new feature, prep for a  feat, etc etc.

example body:

    add the getX query to support x feat
    remove button as ruquest from ticket x
    relayout for better UX

## Format

Please write changesets in below form

```
---
"package-name": patch|minor|major
---
<newline>
<header>
<body>
<footer>
```

> Changesets are markdown files, therefore, line sensitive, please be conscious in adding newlines, the only `newline` should be between the `---` and the `<header>`

### :x: BAD

```
---
"web": patch
"api": patch
---

feat(): add new field fieldX in modelY

- api
  - update resolver X

- web
  - include fieldX in display

IL-999
```

### :white_check_mark: GOOD

```
---
"web": patch
"api": patch
---

feat(): add new field fieldX in modelY
- api
  - update resolver X
- web
  - include fieldX in display
- IL-999
```

### :x: BAD

```
---
"web": patch
---

feat(): add new field fieldX in modelY

IL-999
```

### :white_check_mark: GOOD

```
---
"web": patch
---

feat(): add new field fieldX in modelY
- IL-999
```
