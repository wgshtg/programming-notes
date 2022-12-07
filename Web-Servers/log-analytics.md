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

## 計算每小時有多少請求

```sh
cat access.log | cut -d[ -f2 | cut -d] -f1 | awk -F: '{print $2":00"}' | sort -n | uniq -c
```

```stdout
    30 06:00
    30 07:00
    30 08:00
    32 09:00
    91 10:00
    34 11:00
    30 12:00
    10 13:00
```

## 計算每分鐘有多少請求

```sh
cat access.log | cut -d[ -f2 | cut -d] -f1 | awk -F: '{print $2":"$3}' | sort -nk1 -nk2 | uniq -c
```

```stdout
  1 10:28
  1 10:32
 12 10:34
  1 10:36
 20 10:37
  1 10:38
  1 10:40
```

## 計算每分鐘有多少特定網址請求

```sh
grep "/cas/login" access.log | cut -d[ -f2 | cut -d] -f1 | awk -F: '{print $2":"$3}' | sort -nk1 -nk2 | uniq -c
```

```stdout
    2 09:30
   13 10:37
    1 10:50
    2 11:59
```
