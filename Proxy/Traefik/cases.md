# Traefik 常見配置與使用情境

## 啟用日誌配置

```yml
traefik:
  image: traefik
  command:
    - --accesslog=true
    - --accesslog.filepath=/var/log/access.log
    # 預設日誌格式為 Common Log Format(CLF)
    # --log.format=json
    - --log.level=info
  environment:
    - TZ=Asia/Taipei
  volumes:
    # 將容器目錄掛載到本機目錄
    - ./traefik/log:/var/log
```

## 啟用日誌輪轉

透過 [[logrotate]] 來達成，以下是 `logrotate` 配置檔案內容

```sh
# 注意 log 目錄權限要設定為 644 避免顯示錯誤
# error: skipping "/opt/docker/traefik/log/access.log" because parent directory has insecure permissions
/opt/docker/traefik/log/access.log
{
    rotate 90
    daily
    compress
    missingok
    notifempty
    create 0644 {user} {group}
    sharedscripts
    postrotate
        # 終止容器執行
        docker kill --signal="USR1" {traefik container}
    endscript
}
```

> Container restart policy 需要設為 `unless-stopped`

