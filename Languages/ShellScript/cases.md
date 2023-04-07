# Shell Script 常見配置與使用情境

## 檔案描述符 (File descriptor)

`File descriptor` 是一個用於表述指向檔案的參照，例如：管道 (`pipe`) 或是網路插座 (`Network Socket`) 的抽象化概念，標示在每個程序上。通常是用正整數表示，負數表示無值 (`no value`) 或錯誤情況。

白話文
> `File descriptor` 是用於描述已開啟檔案、管道、網路插座等 I/O 資源的正整數。每個程序 (`process`) 都會擁有一個 `file descriptor table`，該表格維護著程序 `process` 使用的所有 `file descriptors`。
> 程序可以使用這些 `file descriptor` 來進行讀取、寫入、網路連線等操作。

一般會有三種標準 `file descriptor`

| Value | Name            | <stdio.h>file Stream |
|-------|-----------------|----------------------|
| 0     | Standard Input  | stdin                |
| 1     | Standard Output | stdout               |
| 2     | Standard Error  | stderr               |

## 重新導向使用方法

將各種標準流 (`standard streams`) 重新導向到指定位置

```sh
# 將 date stdout 輸出到 log.txt
# log.txt 內容會被完全取代
# log.txt content
# 123
date > log.txt
# log.txt content
# 2023年 4月 7日 週五 15時53分17秒 CST

# 將 date stdout 輸出到 log.txt，插入至檔案內容末尾
date >> log.txt
# log.txt content
# 123
# 2023年 4月 7日 週五 15時53分17秒 CST

# 將 log.txt 內容作為 stdin，讓 grep 搜尋特定字串
grep 1 < log.txt
# output
# 123
grep a < log.txt
# output (empty)

# 使用 << 建立文本區塊 (here document) 的輸入，使用 EOF 標記文本區塊的結束
# EOF 可以用其他任意不包含空格和 tab 字元的字串代替
grep a << EOF

# output
# heredoc> a
# heredoc> b
# heredoc> EOF
# a
```

### 管道 (Piping)

```sh
# 將 cat 標準輸出傳遞給 grep 搜尋符合特定字串 a
# log.txt content
# aaa
cat log.txt | grep a
# output
# aaa
```

## 標準錯誤重新導向

```sh
# 2 是指標準錯誤，重新導向 log.txt
date2 2> log.txt
# output (empty)
# log.txt content
# zsh: command not found: date2

# 將標準錯誤重新導向到標準輸出
date2 2>&1 log.txt
# output
# zsh: command not found: date2
# log.txt content(empty)

# 將標準錯誤重新導向到標準輸出，標準輸出導向到 log.txt
date2 > log.txt 2>&1
# output (empty)
# log.txt content
# zsh: command not found: date2
```
