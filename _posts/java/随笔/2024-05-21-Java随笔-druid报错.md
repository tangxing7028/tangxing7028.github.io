---
layout: post
title: 报错 execute error. SELECT 1 FROM DUAL
categories: Java
description: none
keywords: Java, 系统报错, 报错
---

## 前言

如下图所示，在启动之后系统发生报错

<center>
    <img src="/images/posts/blog/java/Java随笔/druid报错.png" alt="picture not found" style="zoom:80%;" />
    <br>
</center>

修改配置信息：

```xml
testOnBorrow: true
```

参考链接：

[每隔一段时间不操作 再次请求数据库就会报错 execute error. SELECT 1 FROM DUAL，还有Communications link failure · Issue #5806 ](https://github.com/alibaba/druid/issues/5806)
