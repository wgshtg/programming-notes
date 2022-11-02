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
