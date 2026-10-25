---
title: '通过Docker Compose快速部署Vaultwarden'
published: 2026-07-20
description: '通过Docker Compose快速部署Vaultwarden'
image: 'https://im.124365.xyz/file/20260720/1784539118705_large_v-trans.png'
tags: [Docker, 绿联NAS, Docker Compose]
category: Docker
draft: false
---

Vaultwarden 是 Bitwarden Server 的非官方实现（社区项目），主打资源占用低、部署简单，适合个人/小团队自托管密码库。与官方 Bitwarden Server 不同，Vaultwarden 是完全开源的，你可以在自己的服务器上运行它，而无需支付任何费用。

·适合：个人密码管理、多端同步、家庭/小团队共享
·不适合：强合规要求、需要官方企业功能/审计/支持的场景

#### 通过Docker Compose快速部署Vaultwarden

```js
services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    environment:
      DOMAIN: "https://**.124365.xyz"
    volumes:
      - ./vw-data/:/data/
    ports:
      - 192.168.1.7:8086:80
```

