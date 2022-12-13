# JavaScript 解決問題集

## 基本分頁功能

```javascript
let page = '1';
let pageSize = '10';

[].slice((page - 1) * pageSize, page * pageSize);
```
