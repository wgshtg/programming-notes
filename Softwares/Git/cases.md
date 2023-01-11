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

## Configure global gitignore

從 `Git` 中排除常見在作業系統、`IDE` 或框架會產生或使用的檔案

```sh
# macOS
git config --global core.excludesfile ~/.gitignore

# Windows
git config --global core.excludesfile "%USERPROFILE%\.gitignore"
```

```.gitignore
# Mac
.DS_Store

# Windows
Thumbs.db

# etc...
```

## 修改所有 commit 的 committer 和 author

```sh
#!/bin/sh
git filter-branch --env-filter '
OLD_EMAIL="{old-email}"
CORRECT_NAME="{new-author-name}"
CORRECT_EMAIL="{new-author-email}"

if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

[1]:https://git-scm.com/docs/git-config#_conditional_includes
