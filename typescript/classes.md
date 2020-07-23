# TypeScript Classes Overview

_notes taken from [this freeCodeCamp article](https://www.freecodecamp.org/news/the-definitive-typescript-handbook/)_

- We can add types to properties and method arguments

```ts
class Greeter {
  greeting: string;
  constructor(message: string) {
    this.greeting = message;
  }
  greet(name: string) {
    return `Hi ${name}, ${this.greeting}`;
  }
}
```

## Access Modifiers

_TS supports `public`, `private`, and `protected` modifiers_

- `public` works the same as plain JS members and is the default modifier
- `private` cannot be accessed from outside of its containing class
- `protected` members differ from `private`, as it can also be accessed within deriving classes

| Accessible On: | public | protected | private |
| -------------- | ------ | --------- | ------- |
| class          | yes    | yes       | yes     |
| class children | yes    | yes       | no      |
| class instance | yes    | no        | no      |

## Readonly Modifier

_a `readonly` property must be initialized in their declaration or in the constructor_

```ts
class Spider {
  readonly name: string;
  readonly numberOfLegs: number = 8;
  constructor(theName: string) {
    this.name = theName;
  }
}
```

## Parameter Properties

_**parameter properties** let you create and initialize a member in one place_

```ts
class Spider {
  readonly numberOfLegs: number = 8;
  constructor(readonly name: string) {
    // ...
  }
}
```

## Abstract

> the abstract keyword can be used both for classes and for abstract class methods

- **Abstract Classes** cannot be directly instantiated. They are mainly for inheritance where the class which extends the abstract class must define all the abstract methods
- **Abstract Members** do not contain an implementation, thus cannot be directly accessed. These members must be implemented in child classes (_kind of like an interface_)
