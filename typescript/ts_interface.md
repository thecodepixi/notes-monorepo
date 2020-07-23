## TypeScript Interface Overview

_notes taken from [this freeCodeCamp article](https://www.freecodecamp.org/news/the-definitive-typescript-handbook/)_

Interfaces allow us to specify in a single named annotation exactly what properties to expect with its respective type annotations.

_interfaces have zero runtime JS impact. they are used solely for type checking._

- You may declare **optional properties** by marking them with a `?`
- You may declare **read only properties**

```ts
interface ICircle {
  readonly id: string;
  center: {
    x: number;
    y: number;
  };
  radius: number;
  color?: string; // optional property
}

const circle1: ICircle = {
  id: '001',
  center: { x: 0 },
  radius: 8,
}; /* Error! Proper y is missing! */

const circle2: ICircle = {
  id: '002',
  center: { x: 0, y: 0 },
  radius: 10,
}; // OK

circle2.color = '#666'; // sets optional property
circle2.id = '003'; /* Error! cannot assign readonly property */
```

## Extending Interfaces

- Interfaces can extend one or more interfaces, which allows them to be flexible and reusable.

```ts
interface ICircleWithArea extends ICircle {
  getArea: () => number;
}

const circle3: ICircleWithArea = {
  id: '003',
  center: { x: 0, y: 0 },
  radius: 6,
  color: '#fff',
  getArea: function () {
    return this.radius ** 2 * Math.PI;
  },
};
```

## Implementing an Interface

- a class implementing an interface needs to strictly conform to the structure of the interface

```ts
interface IClock {
  currentTime: Date;
  setTime(d: Date): void;
}

class Clock implements IClock {
  currentTime: Date = new Date();
  setTime(d: Date) {
    this.currentTime = d;
  }
  constructor(h: number, m: number) {}
}
```
