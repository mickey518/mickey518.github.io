---
title      : "Docker WordPress超过了站点的最大上传限制"
date       : 2022-04-23 08:00:00 +0800
tags       : Docker WordPress
categories : Docker
toc        : true
---

> 转载：[https://blog.csdn.net/j84491135/article/details/105977073](https://blog.csdn.net/j84491135/article/details/105977073)

## 前言

wordpress容器默认上传限制为2M，这实在是太少了，本文介绍如何修改docker中wordpress的上传限制。

## 步骤

### 1. 进入wordpress容器

```bash
# wordpress是你wordpress的容器id或名称
docker exec -it wordpress /bin/bash
```

### 2. 复制php.ini

```bash
# 复制配置文件，以便php配置生效
cp /usr/local/etc/php/php.ini-production /usr/local/etc/php/php.ini
```

### 3. 修改php.ini

```bash
vim /usr/local/etc/php/php.ini
```

找到以下三个关键值，修改成你想要的值。

注意`memory_limit`>`post_max_size`>`upload_max_filesize`

PS：`vim`查找命令为:`/要查找的字符串`，`n`下一个，`N`上一个

```bash
# 文件大小限制
upload_max_filesize = 200M
# post大小限制
post_max_size = 250M
# 内存占用限制
memory_limit = 500M
```

### 4. 重启容器

```bash
docker restart wordpress
```

---
