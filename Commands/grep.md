# grep 指令說明與常見用法

grep: globally search a regular expression and print，以正規表示式進行全域尋找以及列印

## 查詢條件包含 `"`

```sh
# double quotes with double quotes
echo "\"member\":\"time\"" | grep -e "member\""

# double quotes with single quote
echo '"member":"time"' | grep -e 'member"'
```
