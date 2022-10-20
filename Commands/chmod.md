# chmod 指令說明與常見用法

`change mode`，用來修改檔案和目錄權限

參考資料：

- [File-system permissions Wiki](https://en.wikipedia.org/wiki/File-system_permissions)

```sh
# Read(r): 4, Write(w): 2, Execute(x): 1
# -rw-r-xr-- : user(owner) can read, write; group can read, execute; other can read
# -rw-r-xr-- => ugo: 654
chmod 655 file
```

## 新增檔案和目錄時，套用當層目錄群組權限

```sh
# SGID: Set group ID permission
# 設定 SGID 權限
chmod g+s directory
# 移除 SGID 權限
chmod g-s directory
```
