# tar 指令說明與常見用法

`tar`: `tape archive`，原意將檔案備份到磁帶上，用途是將多個檔案、目錄合併為一個檔案，壓縮後的檔案稱為 `tarball`

## 壓縮資料夾

```sh
tar -cf backup.tar folder
# output
# ./backup.tar
```

## 排除特定檔案被壓縮至壓縮檔案

```sh
# 排除單個檔案
tar --exclude="abc.txt" -cf backup.tar folder

# 排除多個檔案和資料夾
tar --exclude="abc.txt" --exclude="folder1" -cf backup.tar folder

# 排除特定檔案類型
tar --exclude="*.txt" -cf backup.tar folder

# 使用排除檔案
touch exlcude-file.txt
# content of exclude-file.txt
# abc.txt
# folder1
# *.txt
tar -cf backup.tar --exclude-from="exclude-file.txt" folder
tar -cf backup.tar -X exclude-file.txt folder
```

## 檢視壓縮檔內容

```sh
tar -tf backup.tar
```

## 解壓縮檔案

```sh
tar -xf backup.tar
# output
# ./123.txt

tar -xf backup.tar -C /home/backup
# output
# /home/backup/123.txt
```

## 使用 `gzip` 壓縮和解壓縮

```sh
# 加上 -z，--gzip，--gunzip，--ungzip
# 壓縮檔副檔名為 .tar.gz, .taz or .tgz
tar -czf backup.tar.gz folder

tar -xzf backup.tar -C /home/backup
# output
# /home/backup/123.txt
```

## 使用 `Tarpipe`

```sh
# 將建立壓縮檔案的標準輸出串流到另一個 tar 指令的標準輸入作解壓縮
# 可以拿來當作複製當前路徑的檔案到目的路徑
tar -c src-dir | tar -x -C dest-dir
```
