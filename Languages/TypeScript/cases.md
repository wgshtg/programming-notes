# TypeScript 解決問題集

## 當 function parameter 都是 optional，呼叫 function 時指定特定參數

[參考資料](https://bobbyhadz.com/blog/typescript-function-optional-parameters)

```ts
// 一般情況
const func = (param1?: string, param2?: string) => {}
// 錯誤
func(param2: 'string');
// 成功，需要補齊所有 params (不推薦)
func(undefined, 'string');

// 使用 interface 搭配解構
type Prop = {
  param1?: string;
  param2?: string;
}

const func = ({param1, param2}:Prop) => {}
func({param1: '123'});
// 或是
const func = ({param1, param2}:Prop = {}) => {}
func();
```

## 替換字串中所有空白

```ts
const text = ' A BCD ';
text.replaceAll(/\s/g, '');
```

## 指定變數為 Switch 回傳值

技巧為 `Immediately-invoked lambda/function`

```ts
// 用括弧把函式包起來，在用括弧表示函式呼叫
// (() => {})()
// const a = () => {}; a(); // 效果一樣
const number = (() => {switch (1) {
    case 1: return '1';
    case 2: return '2';
    case 3: return '3';
    default: return '0';
}})();
```
