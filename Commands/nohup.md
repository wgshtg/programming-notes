# nohup 指令說明與常見用法

`nohup`: 指的是 `no hang up`。
它在執行指令時，可以忽略 `HUP` 訊號 (SIGHUP: **sign**al **h**ang **up**)，即使使用者登出或中斷終端連接時，指令也不會中斷執行，仍會在背景執行。
預設情況下，`nohup` 會將執行指令所產生的輸出輸出到 `nohup.out` 檔案中。一般使用在當需要執行運行時間較長的程式或指令的情況。

## 使用方式

```sh
# 一般會在後面加上 &，將指令放在背景執行
nohup date &
cat nohup.out
# 2023年 4月 7日 週五 15時53分17秒 CST
```

## 指定輸出檔案

```sh
# 透過 &> 重導向輸出
nohup date &> log.txt &
```