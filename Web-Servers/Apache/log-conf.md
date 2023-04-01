# Apache Log configuration

## Log Rotation 設定

```conf
# 每 24 小時輪轉一次 (86400s)
ErrorLog "|/usr/bin/rotatelogs -l /var/log/error-%Y%m%d.log 86400"
CustomLog "|/usr/bin/rotatelogs -l /var/log/access-%Y%m%d.log 86400" combined
```

## Logging level

依照嚴重程度高到低 `Fatal`, `Error`, `Warn`, `Info`, `Debug`, `Trace`。

| Logging Level | Description |
| --- | --- |
| `Fatal` | 表示致命性錯誤，導致系統、服務提前終止。 |
| `Error` | 表示執行時出現其他錯誤或意外情況，像是功能錯誤，連線異常。 |
| `Warn` | 表示使用已棄用、不當使用的 API，或是運行時發生非預期，但不一定是錯誤的情況。 |
| `Info` | 表示關鍵，有意義的狀態資訊，像是服務啟動狀態，配置啟用停用等。 |
| `Debug` | 表示系統服務執行的詳細資訊，提供開發或測試人員釐清執行狀況或除錯，像是分析效能、錯誤相關。 |
| `Trace` | 表示系統服務執行的詳細資訊，比 `Debug` 更詳細，包含執行的每個步驟。 |

設定 `Logging Level` 時，一般低層級會包含高層級的 `log`，像是配置 `Error` 時，產生的 `log` 會包含 `Error` 和 `Fatal`，`Trace` 會包含以上所有層級的 `log`。
