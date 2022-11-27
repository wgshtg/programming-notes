# Type 和 Interface 的比較

Type(Type Alias): 型別，表示靜態的型別格式
Interface 介面，有彈性的型別表現方式，具意義上的擴充與融合

## Type 介紹

Extensions
> 組合出新的靜態資料型別，而不是實質上的型別擴展

```typescript
type A = { first: number; };
type B = { second: number; };
type C = A & B;
type D = A | B;
let obj: C = { first: 111, second: 222 }; // Correct
let obj: D = { first: 111 }; // Correct
```

## Interface 介紹

Extensions
> 實作符合當前介面的屬性與功能，以及從其他介面擴展來的屬性與功能

```typescript
interface A { first: number }
interface B { second: number }
interface C { first: string }
interface D { second: number }
interface X extends A, B {} // Correct
interface Y extends A, C {} // Error
interface Z extends B, D {} // Correct
```
