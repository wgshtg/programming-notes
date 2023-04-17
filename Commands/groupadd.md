# groupadd 指令說明與常見用法

`groupadd`: 建立群組

群組名稱限制為 `[a-z_][a-z0-9_-]*[$]?`，長度最長為 `32` 字元

- Good: `abc`, `_abc`, `abc123`, `abc-xyz`, `abc$` 👍
- Bad: `$abc`, `123abc`, `abc%` 🙅

在 `Debian` 限制為

- 開頭不能使用：dash(`-`), plus(`+`), tilde(`~`)
- 不能包含字元：colon(`:`), comman(`,`), whitespace(`,`, `\n`, `\t`, etc.)

在 `Ubuntu` 限制為

基本上和 `Debian` 相同，額外增加名稱不能使用全數字 (`fully numeric`)，包含 8 進制 (`octal`) 和 16 進制 (`hexadecimal`)

## 使用方式

```sh
# 建立群組
groupadd {groupname}
# 指定 GID
groupadd -g {GID} {groupname}
```
