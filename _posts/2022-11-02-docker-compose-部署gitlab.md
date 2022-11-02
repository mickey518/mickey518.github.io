---
title      : docker-compose 部署gitlab
date       : 2022-11-02 08:00:00 +0800
categories : Docker
tags       : Docker
classes    : wide
---

使用  `docker-compose` 方式部署 `gitlab` 服务

```yml docker-compose.yml
version: '2'

services:
  gitlab:
    image: gitlab/gitlab-ce:rc
    container_name: gitlab
    restart: always
    environment:
      TZ: Asia/Shanghai
    ports:
      - 22:22
      - 80:80
      - 443:443
    deploy:
      resources:
        limits:
          cpus: "6.00"
          memory: 12G
        reservations:
          memory: 8G
    volumes:
      - ./gitlab/config:/etc/gitlab
      - ./gitlab/gitlab-data:/var/opt/gitlab
      - ./gitlab/gitlab-log:/var/log/gitlab
```