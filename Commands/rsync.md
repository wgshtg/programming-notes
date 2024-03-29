# rsync 指令說明與常見用法

`rsync`: 是一種工具，用來傳輸和同步兩台電腦上的檔案與目錄，利用差分編碼以減少資料網路傳輸量。包含比較檔案修改時間和大小，或校驗碼比較。可以透過 `zlib` 進行資料壓縮，透過 `ssh` 或 `stunnel` 進行加密傳輸。

## 使用方法

```sh
# -a：以遞迴方式同步檔案，並保持檔案屬性、權限、時間戳和連結。
# -v：顯示詳細的進度和統計信息。
# -z：在傳輸時啟用壓縮。
# -r：以遞歸方式同步檔案，但不保持檔案屬性、權限、時間戳和連結。
# --dry-run：模擬同步過程，不會實際同步任何檔案
# --delete: 在同步過程時，同步將不存在來源端的檔案，在目的端刪除
# 預設使用 ssh 登入遠端
rsync -avzh /tmp/123.txt {user}@{ip or host}:/tmp/
```

## 來源端檔案同步至目的端

```sh
rsync -avzh /tmp/123.txt {user}@{ip or host}:/tmp/
```

## 目的端檔案同步回來源端

```sh
rsync -avzh {user}@{ip or host}:/tmp/123.txt /tmp/
```

## 指定 ssh port

```sh
rsync -avzh -e 'ssh -p 2222' /tmp/123.txt {user}@{ip or host}:/tmp/
```
