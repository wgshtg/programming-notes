# scp 指令說明與常見用法

`SCP`: `Secure Copy` 兩台主機透過 `SSH` 來傳輸檔案，同時使用 `SSH` 進行身份認證，確保資料真實性與保密性

## 上傳檔案至伺服器

```sh
scp source-file user@host:directory/target-file
```

## 從伺服器下載檔案

```sh
scp user@host:directory/source-file target-file
```

## 使用指定 port 和私鑰

```sh
scp -P 2222 -i private-key source-file user@host:directory/target-file
```
