## TypeScript Enums Overview

_notes taken from [this freeCodeCamp article](https://www.freecodecamp.org/news/the-definitive-typescript-handbook/)_

> An `enum` (or enumeration) is a way to organize a collection of related values that be numeric or string values

```ts
enum CardSuit {
  Clubs,
  Diamonds,
  Hearts,
  Spades,
}

let card = CardSuit.Clubs;

card = 'not a card suit'; /* Error */
```

_enums are number based **by default** and are 0 indexed_

Enums can alternatively be initialized with string values, which is more readable

```ts
enum SocialMedia {
  Facebook = 'FACEBOOK',
  Twitter = 'TWITTER',
  Instagram = 'INSTAGRAM',
  LinkedIn = 'LINKEDIN',
}
```

## Reverse Mapping

_`enum` supports reverse mapping, which means we can access that value of a member and also a member name from its value_

```ts
const clubsAsNumber: number = CardSuit.Clubs; // 3
const clubsAsString: string = CardSuit[0]; // 'Clubs'
```
