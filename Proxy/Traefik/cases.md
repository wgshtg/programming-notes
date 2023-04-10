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

## 配置 HTTP, HTTPS

```yml
traefik:
  image: traefik
  # 全域設定 HTTP 轉導向 HTTPS
  command:
  - --entrypoints.web.address=:80
  - --entrypoints.websecure.address=:443
  - --entrypoints.web.http.redirections.entryPoint.to=websecure
  - --entrypoints.web.http.redirections.entryPoint.scheme=https
  - --entrypoints.web.http.redirections.entrypoint.permanent=true
  labels:
    - traefik.enable=true
    # HTTPS
    - traefik.http.routers.blog.entrypoints=websecure
    # 啟用 HTTPS TLS 憑證
    - traefik.http.routers.blog.tls=true
    - traefik.http.routers.blog.tls.certresolver={my-resolver}
    # 設定 HTTPS 網域
    - traefik.http.routers.blog.rule=Host(`{domain}`)
    # HTTP
    - traefik.http.routers.blog-insecure.entrypoints=web
    # 設定 HTTP 網域
    - traefik.http.routers.blog-insecure.rule=Host(`{domain}`)
    # 個別設定 HTTP 轉導向 HTTPS
    # 定義 force-secure middleware
    - traefik.http.middlewares.force-secure.redirectscheme.scheme=https
    # 暫時或永久重導向
    - traefik.http.middlewares.force-secure.redirectscheme.permanent=true
    # 設定 blog-insecure router middleware 為 force-secure
    - traefik.http.routers.blog-insecure.middlewares=force-secure
```

## 限制存取規則

限制特定 `IP` 可存取特定路由

```yml
traefik:
  image: traefik
  labels:
    - traefik.enable=true
    - traefik.http.routers.blog-admin.entrypoints=web
    # 限制可存取路由
    - traefik.http.routers.blog-admin.rule=Host(`{domain}`)
    - traefik.http.routers.blog-admin.rule=(Host(`{domain}`) && PathPrefix(`/administrator/`))
    # 限制可存取 IP
    - traefik.http.middlewares.blog-admin-ipwhitelist.ipwhitelist.sourcerange=${ip-whitelist}
    # 設定 blog-admin middleware 為 blog-admin-ipwhitelist
    - traefik.http.routers.blog-admin.middlewares=blog-admin-ipwhitelist
```

