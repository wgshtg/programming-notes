# wc 指令說明與常見用法

`wc`: `word count`，可以讀取標準輸入和檔案內容，來產生統計資訊，包含換列次數、字數、位元組計數，多個檔案可個別計算和總計

## 使用方式

```sh
wc wc.md
# output
#    3       9     115 awk.md
# first column: count of newlines
# second column: number of words
# third column: number of characters(default count by bytes)

# number of characters
wc -m
# number of bytes
wc -c
# Unicode 包含多位元組字符，會造成計算字數結果會不同
```

## 計算中文字數

不建議處理非英文字，計算時會因為 Unicode 編碼和 Non-printable characters (不可打印字符)，與預期字數不同
> 建議寫全英文筆記，就無須計算中文字數~
