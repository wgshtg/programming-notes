# sudo 指令說明與常見用法

全名是 `superuser do`，獲取(管理者)權限，執行特定命令

## 對沒有權限的檔案，使用重定向來更新內容，顯示 `Permission Denied`

```sh
echo > file
# -bash: file: Permission denied
sudo echo > file
# -bash: file: Permission denied
```

> 原因是 `sudo` 只有用 `root` 權限執行 `echo`，而沒有執行重定向 `>`

```sh
# 透過 `sudo` 取得管理者 sh 權限來執行指令
sudo sh -c "echo > file"
# 其他方法
echo | sudo tee file
echo | sudo tee -a file # -a: append, like >>
```
