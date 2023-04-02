# macOS 常見配置與使用情境

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

## 重置 Launchpad (所有應用程式列表)

在 Launchpad 上可以重新排列應用程式，在安裝和移除程式時，排列順序也會更新。在整理上會顯得有點雜亂。
可透過以下指令來重置 Launchpad，預設以內建軟體和套裝軟體顯示在第一頁，第三方軟體在第二頁開始以 App 名稱字母排序。

```sh
# Open Terminal.app
defaults write com.apple.dock ResetLaunchPad -bool true; killall Dock
```
