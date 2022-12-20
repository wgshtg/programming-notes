# JavaScript 解決問題集

## 基本分頁功能

```javascript
let page = '1';
let pageSize = '10';

[].slice((page - 1) * pageSize, page * pageSize);
```

## 將 switch 回傳值指定給變數

```javascript
const variable = (() => {
  switch (1) {
    case 1:
      return 1;
    case 2:
      return 2;
    default:
      return 3;
  }
})();
console.log(variable); // 1
```

### `IIFE` (`Immediately Invoked Function Expression`) 是定義完馬上執行的 `function` 又稱 `Self-Executing Anonymous Function`

`(() => {})`: `()` 裡的是 `anonymous function`
`()()`: 第二個 `()` 表示立刻轉譯 `function`

```javascript
(() => {})();
(async () => {})();
```
