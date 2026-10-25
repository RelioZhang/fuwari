---
title: '通过Docker Compose快速部署Navidrome'
published: 2026-07-20
description: '通过Docker Compose快速部署Navidrome'
image: 'https://im.124365.xyz/file/20260720/1784539118705_large_v-trans.png'
tags: [Docker, 绿联NAS, Docker Compose]
category: Docker
draft: false
---

Navidrome 是一款轻量级、跨平台的开源音乐服务器，支持多种音频格式。

#### 通过Docker Compose快速部署Navidrome

```js
services:
  navidrome:
    image: deluan/navidrome:latest    # 网址被和谐了一部分，具体参考上方图片
    container_name: navidrome-3
    deploy:
      resources:
        limits:
          memory: 512M      # 硬限制：容器能使用的最大内存
        reservations:
          memory: 16M      # 软限制：容器启动时预留的最小内存
    user: 1000:1000 # 启动权限
    ports:
      - "4533:4533"
    restart: unless-stopped
    environment:
      # 使用配置文件，其实最新版默认会读取这个路径，ND_CONFIGFILE 可以删除
      ND_CONFIGFILE: "/data/navidrome.toml"

    volumes:
      - /volume1/docker/navidrome-3/data:/data           # 映射 Navidrome /data/ 路径（缓存、数据库、配置文件，如果不想把缓存映射出来，请手动映射单个文件）
      - /volume4/Music:/music/library1:ro                # 音乐路径1
      # - /volume1/CloudNas/CloudDrive:/music/library2:ro  # 音乐路径2
```

