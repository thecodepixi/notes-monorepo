# More About Types...

_notes taken from [this freeCodeCamp article](https://www.freecodecamp.org/news/the-definitive-typescript-handbook/)_

## Type Assertion

TypeScript allows you to override its inferred types in any way you want to. This is used when you have a better understanding of a variable type than the compiler on its own.

```ts
const friend = {};
friend.name = 'John'; // Error! Property 'name' does not exist on type '{}'

interface Person {
  name: string;
  age: number;
}

const person = {} as Person;
person.name = 'John';
```

## Type Inference

TypeScript infers types of variables when there is no explicit information available in the form of type annotations

```ts
// variable definitions
let a = 'some string';
let b = 1;
a = b; // Error! Type number is not assignable to string

//In case of complex objects, TS looks for the most common type to infer the type of the object
const arr = [0, 1, true, false]; // (number | boolean)[]

// function return types
function sum(x: number, y: number) {
  return x + y; // infer number return type
}
```

## Type Compatibility

Type compatibility is based on structural typing, which relates types based solely on their members.

The rule for structural types is that `x` is compatible with `y` if `y` has the same members as `x`

```ts
interface Person {
  name: string;
}

let x: Person;
let y = { name: 'John', age: 20 }; // type {name: string, age: number}
x = y;
// x is still of type Person
// the following will produce an error because the compiler does not expect the property age to be in Person, but the result will be as expected
console.log(x.age); // 20
```

_since `y` has a member `name: string`, it matched the required properties for the Person interface, making `x` a sub-type of `y'_
