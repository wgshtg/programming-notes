<!-- omit in toc -->
# Import and Export module

引入和導出模組（物件，變數，函式），有 `default` 和 `named` 以下兩種方式。

- [Import](#import)
- [Export](#export)
- [Default import \& export](#default-import--export)
- [Named import and export](#named-import-and-export)
- [Mixing default and named](#mixing-default-and-named)
- [Side effect](#side-effect)
- [Extra](#extra)
- [在 Barrel file (index.ts) 中同時 export default, name modules 時](#在-barrel-file-indexts-中同時-export-default-name-modules-時)

## Import

```javascript
import defaultExport from "module-name";
import * as name from "module-name";
import { export } from "module-name";
import { export as alias } from "module-name";
import { export1 , export2 as alias2 , [...] } from "module-name";
import defaultExport, { export [ , [...] ] } from "module-name";
import defaultExport, * as name from "module-name";
import "module-name"; // import 'A' or import 'A.js'
```

`module-name` 可以是模組的**相對**或**絕對路徑**，某些 bundlers 允許或需要加上副檔名 (`.js` or `.ts`)

## Export

```javascript
export { name1, name2, … };
export { variable1 as name1, variable2 as name2, … };

// 底下的 function 用 class, function, * 也可以
export default expression;
export default function (…) { … }
export default function name1(…) { … }

export { name1 as default, … };
export * from …;
export { name1, name2, … } from …;
export { import1 as name1, import2 as name2, …} from …;
```

## Default import & export

每個模組只能有一個 `default export`
`import name` 可以不用和 `export name` 相同，`import` 會自動解析 `default name`。

```javascript
// A.js
// 只能使用 default 不能使用 var, let, const
export default A = 1;
export default 1;

// B.js
import A from 'A';  // Work
import AA from 'A'; // Work
import { default as AAA } from 'A'; // default export is a named export with name default
console.log(A); // 1
console.log(AA); // 1
```

## Named import and export

每個模組可以有多個 `named export`
`import name` 要和 `export name` 要一樣！

```javascript
// A.js
export const A = 1;
export const AA = 2;

// B.js
import { A } from 'A'; // 從模組 A 引入單一導出物件 A 和其數值
import { AA } from 'A'; // 從模組 A 引入單一導出物件 AA 和其數值
import { A, AA } from 'A'; // 從模組 A 引入數個導出物件 A 和 AA 和各自數值
import { AAA } from 'A' // 模組 A 並沒有導出名稱為 AAA 的物件，故無法引入
```

## Mixing default and named

```javascript
// A.js
export default A = 1;
export const AA = 2;
export const AAA = 3;

// B.js
import A, { AA, AAA } from 'A'; // default 需要寫在第一個
import A, { AA as XX, AAA as XXX } from 'A' // 重新命名導出模組

import * as X from 'A'; // 指定 X 為導出命名空間，包含所有導出物件 A, AA, AAA
console.log(X); // {default: 1, AA: 2, AAA: 3}
```

## Side effect

```javascript
import 'A.js';
```

## Extra

> 在使用 `named import` 時，會使用 `{}`，`default import` 則不使用

## 在 [Barrel file][1] (index.ts) 中同時 export default, name modules 時

```typescript
import Button from './buttons';
export * from './buttons';
export { Button };
```

[1]: https://github.com/basarat/typescript-book/blob/master/docs/tips/barrel.md
