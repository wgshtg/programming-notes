# Log 常見分析

## 常見 Log 資料格式

```log
172.18.0.1 - - [29/Nov/2022:13:18:52 +0800] "POST /account/login/cas HTTP/1.1" 401 134 "-" "Apache-HttpClient/4.5.13 (Java/11.0.17)" 11934 "account@docker" "http://172.18.0.16:8080" 7ms
```

## 計算每個 IP 的請求次數

```sh
# uniq 過濾連續重複字串，需要先用 sort 排序
awk '{print $1}' access.log  | sort | uniq -c | sort -nr | head
```

```stdout
  398 172.18.0.1
   41 192.168.48.12
   19 192.168.48.24
    2 192.168.48.25
    2 192.168.102.5
    2 10.3.82.71
    1 192.168.48.70
    1 192.168.1.108
```
