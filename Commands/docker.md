# docker 指令說明與常見用法

## 總計所有容器記憶體使用量

```sh
# no-stream 只取第一次輸出內容 --format 只輸出記憶體使用欄位(例如: 66.88MiB / 3.7GiB)
# awk 抓取每列記憶體使用量(使用 MiB 分隔)
# sed 把 GiB 和 KiB 換成相對於 MiB 的倍數和除數(例如: 6GiB 變成 6 * 1024)
# bc 做數學運算
# 最後 awk 合計每列數值
# 單位為 MiB
docker stats --no-stream --format '{{.MemUsage}}' | awk '{print $1}' | sed 's/GiB/ * 1024/;s/MiB//;s/KiB/ \/ 1024/' | bc -l | awk '{sum+=$1} END {print sum}'

# 單位為 GiB
docker stats --no-stream --format '{{.MemUsage}}' | awk '{print $1}' | sed 's/GiB//;s/MiB/ \/ 1024/;s/KiB/ \/ 1024^2/' | bc -l | awk '{sum+=$1} END {print sum}'
```
