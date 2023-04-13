# docker 常見配置與使用情境

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

## 移除 `dangling` `images`

`dangling` 意思是 `image` `name` 或 `tag` 為 `none`

常出現 `dangling` `image` 的情況如下

- 更新舊有 `image` 時，`tag` 會變成 `none`
- 建置相同 `tag` 的 `image` 時，舊有的 `image` `tag` 會變成 `none`

```sh
# 清除 dangling image
docker image prune
# output
# WARNING! This will remove all images without at least one container associated to them.
# Are you sure you want to continue? [y/N] y

# 清除 dangling image，略過確認
docker image prune --force
docker image prune -f

# 清除 dangling image 包含未被容器使用 image
docker image prune -a
```
