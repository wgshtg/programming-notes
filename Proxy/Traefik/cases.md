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

