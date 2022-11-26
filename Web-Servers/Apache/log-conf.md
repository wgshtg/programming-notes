# Apache Log configuration

## Log Rotation 設定

```conf
# 每 24 小時輪轉一次 (86400s)
ErrorLog "|/usr/bin/rotatelogs -l /var/log/error-%Y%m%d.log 86400"
CustomLog "|/usr/bin/rotatelogs -l /var/log/access-%Y%m%d.log 86400" combined
```
