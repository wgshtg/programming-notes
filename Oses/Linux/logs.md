# Linux Logs

## 常見的 Log 分類

### System Logs

系統日誌，包含系統操作、啟動訊息，核心訊息、硬體事件，用來監視系統效能和故障排除。

- `/var/log/dmesg`: 和設備驅動有關
- `/var/log/syslog`(`Ubuntu`, `Debian`) 或 `/var/log/messages`(`CentOS`,`Redhat`): 由 `syslog` `deamon` 產生，包含系統內所有活動紀錄📓

### Application Logs

應用程式日誌，包含應用程式行為，有 `errors`, `warnings`, `info` 等。用來診斷應用程式問題和分析效能。

### Service Logs

服務日誌，包含系統上執行的服務，包含網路和背景服務。用來監測服務活動和最佳化服務效能。

### Event Logs

事件日誌，包含系統事件，像是帳號登入，系統關機，安全性事件。用來稽核系統活動，追蹤帳號活動和研究安全事件。

- `/var/log/faillog`: 包含所有登入失敗的資訊
- `/var/log/auth.log`(``Ubuntu`,`Debian`) 或`/var/log/secure`(`CentOS`,`Redhat`): 包含帳號驗證成功，失敗和方式的紀錄

## 參考連結

[What are Linux Logs? Code Examples, Tutorials & More](https://stackify.com/linux-logs/)
