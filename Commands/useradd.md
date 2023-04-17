# useradd 指令說明與常見用法

`useradd`: 建立帳號

帳號名稱限制為 `[a-z_][a-z0-9_-]*[$]?`

- Good: `abc`, `_abc`, `abc123`, `abc-xyz`, `abc$` 👍
- Bad: `$abc`, `123abc`, `abc%` 🙅

配置檔 `/etc/login.defs`

- 帳號建立、登入和密碼政策等配置

## 使用方式

```sh
# 建立帳號
useradd {username}
# 加入到特定單一群組
useradd -g {groupname or groupid} {username}
# 加入到特定群組列表
useradd -G {group1-name or group1-id},{group2-name or group2-id}
# 指定 UID
useradd -u {uid} {username}
# 同時建立與帳號名稱相同的群組，並加入至該群組
useradd -U {username}
```
