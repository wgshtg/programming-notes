# addgroup 指令說明與常見用法

`addgroup`: 建立群組

- `/etc/adduser.conf`: `adduser`, `addgroup` 預設配置檔
- `/usr/local/sbin/adduser.local`: 客製化的附加配置

## 使用方式

```sh
# 建立群組
addgroup {groupname}
# 指定 GID
addgroup {GID} {groupname}
```
