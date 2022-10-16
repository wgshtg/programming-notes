# Find 指令說明與常見用法

## 說明

```sh
# 列出當前目錄下所有檔案與目錄
# Type f: file, type d: directory
find . -type [f|d] -name '*'
```

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
