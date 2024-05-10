---
layout: post
title: Java随笔
categories: Java
description: none
keywords: Java, Https, 报错
---

## 前言



`HttpClient javax.net.ssl.SSLPeerUnverifiedException: Certificate doesn't match` 错误解决办法

这个报错意思是，请求的`URL`是`HTTPS`的，但是`ssl`证书和实际的主机域名不匹配，手工覆盖默认的校验规则即可。

<center>
    <img src="/images/posts/blog/Java随笔/安全链接.png" alt="picture not found" style="zoom:80%;" />
    <br>
</center>

参考链接：

[[ 错误解决办法](https://blog.csdn.net/tianxue04/article/details/98957670)]
