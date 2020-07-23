# TypeScript Functions Overview

_notes taken from [this freeCodeCamp article](https://www.freecodecamp.org/news/the-definitive-typescript-handbook/)_

> We can add types to each of the parameters and to the functions return type:

```ts
function add(x: number, y: number): number {
  return x + y;
}
```

## Function Overloads

_TS allows you to declare **function overloads**_

```ts
function padding(a: number, b?: number, c?: number, d?: number) {
  if (b === undefined && c === undefined && d === undefined) {
    b = c = d = a;
  } else if (c === undefined && d === undefined) {
    c = a;
    d = b;
  }
  return {
    top: a,
    right: b,
    bottom: c,
    left: d,
  };
}
```

_the meaning of each parameter changes based on how many parameters are passed. this function only allows one, two or four parameters. to create function overload, you just declare the function header multiple times. the last function header is the one that is actually active **within** the function body, but is not available to the outside world_

```ts
function padding(all: number);
function padding(topAndBottom: number, leftAndRight: number);
function padding(top: number, right: number, bottom: number, left: number);
function padding(a: number, b?: number, c?: number, d?: number) {
  if (b === undefined && c === undefined && d === undefined) {
    b = c = d = a;
  } else if (c === undefined && d === undefined) {
    c = a;
    d = b;
  }
  return {
    top: a,
    right: b,
    bottom: c,
    left: d,
  };
}

padding(1);
padding(1, 1);
padding(1, 1, 1, 1);
padding(1, 1, 1); /*Error! wrong number of args*/
```

## Number of Arguments

_we need to pass in at least enough arguments to a function call, but extra arguments will not cause errors_

```ts
function consoleName(person: Person) {
  console.log(person.name);
}
consoleName({ name: 'John' }); // 'John'
consoleName({ name: 'John', age: 30 }); // 'John', extra argument is ignored
```

## Return Type

_return type must contain at least enough data_

```ts
let x = () => ({ name: 'John' });
let y = () => ({ name: 'John', age: 30 });
x = y; // OK
y = x; // Error! property age is missing from x
```
