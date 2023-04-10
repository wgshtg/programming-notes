# logrotate 指令說明與常見用法

`logrotate`: 是一個日誌檔案管理工具，用來簡化大量被產生的日誌檔案的管理，允許日誌自動輪換、壓縮、刪除和郵寄，設定在每天、每週、每月或檔案大小等條件下處理。

## 使用方式

預設配置檔案路徑為：`/etc/logrotate.conf`
其他配置檔案目錄路徑為：`/etc/logrotate.d`

### 配置檔案內容範例

```sh
# 可同時配置多個 log path 或使用 *
{log-path}
{log-path2}
{
    # 最多保留日誌檔案數量
    rotate {number}
    # 運行週期：daily, weekly, monthly, yearly
    daily
    # 啟用壓縮
    # 不啟用壓縮 nocompress
    compress
    # 找不到日誌檔案時不發出錯誤
    missingok
    # 如果日誌檔案內容為空
    notifempty
    # 建立新的日誌檔案，並設定擁有者和權限
    # 日誌檔案名稱與被輪轉的日誌檔案名稱相同
    create 0640 {user} {group}
    # 每次輪轉時都會執行 prerotate 和 postrotate (可能有多個符合條件的日誌需要被輪轉)
    # 啟用 sharedscripts 後只會在全部輪轉後只執行一次 prerotate 和 postrotate
    sharedscripts
    # 完成日誌轉換後要執行的指令，通常是讓存取該日誌的服務重新載入、讀寫日誌
    # postrotate 和 endscript 是一組
    postrotate
        {command restart or reload}
    endscript
}
```

### 測試配置檔案可否正常執行

```sh
logrotate /etc/logrotate.conf --force
```
