---
title: '通过Docker Compose快速部署Flatnas'
published: 2026-07-20
description: '通过Docker Compose快速部署Flatnas'
image: 'https://im.124365.xyz/file/20260720/1784539118705_large_v-trans.png'
tags: [Docker, 绿联NAS, Docker Compose]
category: Docker
draft: false
---

FlatNas 是一个轻量级、高度可定制的个人导航页与仪表盘系统。它基于 Vue 3 与 Go(Gin) 构建，旨在为 NAS 用户、极客和开发者提供一个优雅的浏览器起始页。

#### 通过Docker Compose快速部署Flatnas

```js
version: "3.8"

services:
  flatnas:
    image: qdnas/flatnas:latest
    container_name: flatnas
    restart: unless-stopped
    ports:
      - "23000:3000"
    volumes:
      - ./data:/app/server/data #指定路径下新建data
      - /volume4/Music:/app/server/music #映射播放器路径
      - ./PC:/app/server/PC #映射背景路径
      - ./APP:/app/server/APP #映射移动端背景路径
      - ./doc:/app/server/doc #映射文件传输助手路径
      - /var/run/docker.sock:/var/run/docker.sock #映射Docker Socket
```

![图片1](https://im.124365.xyz/file/20260720/1784532578290_flatnas-1.png)
![图片2](https://im.124365.xyz/file/20260720/1784532589489_flatnas-2.png)
![图片3](https://im.124365.xyz/file/20260720/1784532592962_flatnas-3.png)