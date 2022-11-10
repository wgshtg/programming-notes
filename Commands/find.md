# find 指令說明與常見用法

## 找出最近一個禮拜修改的檔案

```sh
#  -mtime [-|+]n[s|m|h|d|w]
# -: 在..時間內, +: 在..時間前
# s:second, m:minute, h:hour, d:day, w:week
find . -type f -mtime -4w

# Output
# ./file1
# ./file2
# ./directory

# 透過 ls 顯示詳細資訊
find . -type f -mtime -4w -ls
# 27035483  24 -rw-r--r--  1 user group  8196 10 12 11:02 ./file1
```

## 排除特定資料夾

搜尋當前相對或絕對路徑下檔案或資料夾，用排除路徑字串來過濾查詢路徑

`-not -path "..." -not -path "..."` 可以疊加

```sh
# project
# |---- node_modules
#       |---- nma.js
#       |____ nmb.js
# |----a.js
# |----b.js
# current path: project
# 相對路徑
find . -name "*.js" -not -path "./node_modules/*"

# 絕對路徑
find project -name "*.js" -not -path "project/node_modules/*"

# 排除所有和 node_modules 有關的路徑
find . -name "*.js" -not -path "*/node_modules/*"
```
