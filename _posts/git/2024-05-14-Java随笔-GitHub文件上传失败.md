---
layout: post
title: GitHub文件上传失败
categories: Git
description: none
keywords: Git, 报错
---


第一天使用vpn上传文件还是正常的，第二天发现报错，上传失败，失败内容如下:
报错内容: fatal unable to access ‘httpsgithub.comxxxxxxxxxxx.git’ Recv failure Connection was reset
解决方案：编辑系统代理，查看端口号
<center>
    <img src="/images/posts/blog/java/Java随笔/代理.png" alt="picture not found" style="zoom:80%;" />
    <br>
</center>

打开git，输入：git config --global http.proxy http://127.0.0.1:端口号

以上，问题解决，已经可以正常上传文件

参考链接：

[[ 错误解决办法](https://blog.csdn.net/hggjjkk/article/details/130528271)]
