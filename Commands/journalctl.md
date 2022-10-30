# journalctl 指令說明與常見用法

參考：<https://www.peterdavehello.org/2020/01/clean-up-linux-systemd-journal-logs/>

## 清理 systemd-journald log，釋放硬碟空間

```sh
# 查看 journalctl 空間使用上限 (預設硬碟總空間的 1 成)
journalctl --disk-usage
# output
# Archived and active journals take up 1.0G in the file system.

# 清除特定時間以前的 journal (30 天以前)
journalctl --vacuum-time=30d
# output
# Deleted archived journal /var/log/journal/562ce60b9555430b8a6c0afbfdd20024/system@0005e994d4a7d761-3a52e903f10f45e9.journal~ (8.0M).
# ...
# Deleted archived journal /var/log/journal/562ce60b9555430b8a6c0afbfdd20024/system@53c3926538a147558e94c9e5b2075b4c-0000000000000001-0005e994e7d1c3ba.journal (32.0M).
# Vacuuming done, freed 864.1M of archived journals from /var/log/journal/562ce60b9555430b8a6c0afbfdd20024.
```
