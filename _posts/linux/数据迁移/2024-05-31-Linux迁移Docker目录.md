---
layout: post
title: Docker目录迁移
categories: Linux
description: none
keywords: Linux, docker, 目录迁移
---

## 前言
预发环境，以前只有一个系统盘，数据都存放在系统盘中，现在进行整改，将docker目录迁移到数据盘中。

1. 查看docker安装目录

   ```shell
   sudo docker info | grep "Docker Root Dir"
   # [out] Docker Root Dir: /var/lib/docker
   ```

2. 停止docker服务

   ```shell
   sudo systemctl stop docker.socket
   sudo systemctl stop docker
   ```

3. 创建需要迁移的目录

   ```shell
   sudo mkdir -p /data1/lib
   ```

4. 复制docker安装内容/var/lib/docker 到新的目录

   ``` shell
   sudo mv -r /var/lib/docker /data1/lib
   ```

5. 创建软连接

   ```shell
   sudo ln -s /var/lib/docker /data1/lib/docker
   ```

6. 重启docker

   ```shell
   sudo systemctl restart docker
   ```

## 【参考】

[docker查看安装路径以及修改安装路径 - Dark华 - 博客园 (cnblogs.com)](https://www.cnblogs.com/DarkRoger/p/16575840.html)
