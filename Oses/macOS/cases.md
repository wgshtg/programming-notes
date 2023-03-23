# 問題集錦

## 環境變數設定位置

1. `~/.bash_profile`, `~/.bashrc`, `.zshrc` 或其他 `shell profile`，內容範例如下

```sh
export VARIABLE_NAME=value;
```

2. `/etc/paths`, `/etc/paths.d`

在路徑下建立任意檔名的檔案，不包含副檔名，例如建立 `/etc/paths.d/dotnet`，內容如下

```sh
/usr/local/share/dotnet
```

更新完檔案後，重開終端機，該路徑會自動更新到 `PATH` 環境變數中
