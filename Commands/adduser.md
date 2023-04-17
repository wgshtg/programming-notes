# adduser 指令說明與常見用法

`adduser`: 建立帳號，自動建立和加入與帳號名稱相同的家目錄、預設 `Shell`，交互式設置密碼

- `/etc/adduser.conf`: `adduser`, `addgroup` 預設配置檔
- `/usr/local/sbin/adduser.local`: 客製化的附加配置

## 使用方式

```sh
# 建立帳號
adduser {username}
# 指定家目錄位置
adduser --home {home-path} {username}
# 指定登入 shell
adduser --shell {shell-path} {username}
# 取消自動建立家目錄
adduser --no-create-home {username}
# 停用密碼，可以透過 SSH keys 登入
adduser --disabled-password {username}
# 停用登入，建立帳號時，不設定密碼。帳號會一直無法使用，直到密碼被設定
adduser --disabled-login {username}
```
