# TypeScript Types Overview

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

### Never

_`never` represents the type of values that never occur. `never` is the return type of a function that will always throw an exception or not reach its end point_

```ts
// throws an exception
function error(message: string): never {
  throw new Error(message);
}

// unreachable end point
function continuousProcess(): never {
  while (true) {
    //...
  }
}
```

### Null and Undefined

_both `undefined` and `null` have their own types, like `void` they're very useful on their own but become useful when used within union types_

```ts
type someProp = string | null | undefined;
```

### Unknown

_introduced in TS 3.0, `unknown` is the type-safe counterpart of `any`. anything is assignable to `unknown`, but `unknown` isn't assignable to anything but itself and `any`. no operations are permitted on an `unknown` without first asserting or narrowing to a more specific type_

```ts
type I1 = unknown & null; // null
type I2 = unknown & string; // string
type U1 = unknown | null; // unknown
type U2 = unknown | string; // unknown
```

### Type Alias

_type alias provides names for type annotations allowing you to use it in several places_

```ts
type Login = string;
```

### Union Type

_TS allows us to use more than one data type for a property_

```ts
type Password = string | number;
```

### Intersection Type

_intersections are types that combine properties of all of the member types_

```ts
interface Person {
  name: string;
  age: number;
}

interface Worker {
  companyId: string;
}

type Employee = Person & Worker; // this is the intersection type

const bestOfTheMonth: Employee = {
  name: 'Emily',
  age: 30,
  companyId: '12345',
};
```
