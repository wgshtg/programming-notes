# source 指令說明與常見用法

`source` 是一個 `Shell` 內建指令，用來在當前 `shell` 中執行檔案內容，與一般用 `sh` 執行檔案，另外建立 `subshell` 執行不同。

> 在 `Bash` 和 `POSIX-ish shells`，可以使用 dot (`.`) 表示
> 當檔案沒有執行權限時，可以透過 `source` 來執行檔案內容

## 使用方式

```sh
cat setEnv.sh
# a=2
echo $a
#
source setEnv.sh
echo $a
# 2
```
