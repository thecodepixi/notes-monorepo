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
| class | yes | yes | yes |
| class children | yes | yes | no |
| class instance | yes | no | no |
