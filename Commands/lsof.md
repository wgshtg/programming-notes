# lsof 指令說明與常見用法

`lsof`: `list open files`，列出所有程序所開啟的檔案。檔案類型包含一般檔案、目錄、連結檔、管線檔、網路插座 (`network sockets`) 和裝置 (`device`) 等等。

## 找出有哪些 port 被監聽

> 執行時需要有管理者權限

```sh
# 列出所有處於 LISTEN 狀態的 TCP 網路連線
lsof -i TCP -s TCP:LISTEN
# output
# COMMAND      PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
# sshd         985            root    4u  IPv6   19678      0t0  TCP *:ssh (LISTEN)
# docker-pr 491658            root    4u  IPv4 2751796      0t0  TCP *:postgresql (LISTEN)
# docker-pr 516451            root    4u  IPv4 2881300      0t0  TCP *:http-alt (LISTEN)
# docker-pr 516479            root    4u  IPv6 2881303      0t0  TCP *:https (LISTEN)
# docker-pr 516493            root    4u  IPv4 2883970      0t0  TCP *:http (LISTEN)

# 不解析 host names 和 port name
lsof -i TCP -s TCP:LISTEN -n -P
# output
# COMMAND      PID            USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
# sshd         985            root    4u  IPv6   19678      0t0  TCP *:22 (LISTEN)
# docker-pr 491658            root    4u  IPv4 2751796      0t0  TCP *:5432 (LISTEN)
# docker-pr 516451            root    4u  IPv4 2881300      0t0  TCP *:8080 (LISTEN)
# docker-pr 516479            root    4u  IPv6 2881303      0t0  TCP *:443 (LISTEN)
# docker-pr 516493            root    4u  IPv4 2883970      0t0  TCP *:80 (LISTEN)
```
