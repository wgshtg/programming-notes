<!-- omit in toc -->
# React Element Types

`ReactElement`，`JSX.Element` 和 `ReactChild` 是相似的都是 `React` 最小單元 `Element`，`ReactNode` 則是包含前面型別，可表示 `Component`，算是更高層級。

- [ReactElement](#reactelement)
- [JSX.Element](#jsxelement)
- [ReactChild](#reactchild)
- [ReactNode](#reactnode)

## ReactElement

底層型別定義，[原始碼參考][1]

```typescript
interface ReactElement<P = any, T extends string | JSXElementConstructor<any> = string | JSXElementConstructor<any>> {
  type: T;
  props: P;
  key: Key | null;
}
```

## JSX.Element

擴展 `ReactElement` 介面，`type`, `props` 型別皆為 `any`，[原始碼參考][2]

```typescript
declare global {
  namespace JSX {
    interface Element extends React.ReactElement<any, any> { }
  }
}
```

## ReactChild

> Deprecated!!

擴展 `ReactElement` 多了 `string`, `number`，讓純文字和數字也能傳入，[原始碼參考][3]

```typescript
type ReactChild = ReactElement | string | number;
```

## ReactNode

`ReactNode` 是一種 `Virtual DOM` 表示，像是一個 `Component`，包含 `Component` 的回傳值。從[定義][4]來看，在 `Component` 中放進 `Sub Component`，傳入 `children` 時，應用 `ReactNode` 來定義其型別，允許多個元素、元件傳入

```typescript
// Definition
type ReactNode = ReactElement | string | number | ReactFragment | ReactPortal | boolean | null | undefined;

// Usage
// A is ReactNode
const A = () => {
  // Return value is ReactElement
  return <p>text</p>;
}
const Item = ({children}: {children: ReactNode}) => <h1>{children}</h1>;
const App = () => <div><Item>{<A />}</Item></div>;

// <div>
//   <h1>
//     <p>text</p>
//   </h1>
// </div>
```

[1]:https://github.com/DefinitelyTyped/DefinitelyTyped/blob/master/types/react/index.d.ts#L146
[2]:https://github.com/DefinitelyTyped/DefinitelyTyped/blob/master/types/react/index.d.ts#L3126
[3]:https://github.com/DefinitelyTyped/DefinitelyTyped/blob/master/types/react/index.d.ts#L224
[4]:https://github.com/DefinitelyTyped/DefinitelyTyped/blob/master/types/react/index.d.ts#L231
