# cut 指令說明與常見用法

## 擷取欄位資料

```sh
# -d delimiter, field delimiter character
# -f field, list specifies fields
echo 1,2,3,4 | cut -d, -f2
# output
# 2
```
