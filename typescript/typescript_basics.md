# TypeScript Overview

_notes taken from [this freeCodeCamp article](https://www.freecodecamp.org/news/the-definitive-typescript-handbook/)_

## What is TypeScript

- a statically typed superset of JS
- aims to ease development of large JS apps
- AKA: _javascript that scales_

## Why use TypeScript?

- Type systems increase code quality, readability, and make it easier to maintain and refactor your codebase.
- Errors can be caught at compile time instead of runtime.

**TypeScript Pros**

- Catch errors earlier in dev cycle
- Manage large codebases
- Easier refactoring
- Easier to work in teams

**TypeScript Cons**

- It's something additional to learn
- Type errors can be inconsistent
- Configuration drastically changes behavior

## Types

### Boolean

```ts
const isLoading: boolean = false;
```

### Number

```ts
const decimal: number = 8;
const binary: number = 0b110;
```

### String

```ts
const fruit: string = 'orange';
```

### Arrays

_array types can be written two ways_

```ts
// most common
let firstFivePrimes: number[] = [2, 3, 5, 7, 11];
// less common
let firstFivePrimes2: Array<number> = [2, 3, 5, 7, 11];
```

### Tuples

_tuples allow you to express an organized array where the type of a fixed number of elements is known_

```ts
let contact: [string, number] = ['John', 8675309];
contact = ['Emily', 12345, 'extra arg']; /* Error! */
```

### Any

_`any` is compatible with any/all types in the type system_

```ts
let variable: any = 'a string';
variable = 5;
variable = false;
```

### Void

_`void` is the absence of a type, and is used much the same way as it is in java_

```ts
function logSomething(something: string): void {
  console.log(something);
}
```
