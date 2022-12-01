# Git 常用設定與情境解決

## 配置不同專案路徑下設定不同使用者資訊

```conf
; file path: /home/user1/.gitconfig
; 設定要套用的路徑
[includeIf "gitdir/i:~/company/"]
; 設定對應組態檔案
  path = ~/company/company.inc
[includeIf "gitdir/i:~/project/"]
  path = ~/project/project.inc
```

```conf
; file path: /home/user1/company/company.inc
; file path: /home/user1/project/project.inc
[user]
    name = Username
    email = username@user.com
```

[官方文件連結][1]

[1]:https://git-scm.com/docs/git-config#_conditional_includes
