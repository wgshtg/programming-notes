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

