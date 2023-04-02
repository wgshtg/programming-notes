# TypeScript 常見配置與使用情境

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

## 從字串、數字轉成列舉，列舉 key 轉成字串

```ts
enum Tag {
  A,
  B,
  C
}

const tag1 = 'A';
// 把 Tag 轉成型別，再把型別上 key 抓出來，字串再轉型比對 key
Tag[tag1 as keyof typeof Tag] === Tag.A; // true
const tag2 = 0;
Tag[tag2] === Tag.A; // true
Tag[Tag.A] === 'A' // true
```
