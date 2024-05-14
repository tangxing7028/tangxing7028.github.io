---
layout: post
title: @Value无法正常使用
categories: Java
description: none
keywords: Java, 配置文件, 报错
---

## 前言

如下图所示，在Springboot装配xxl-job过程中，发现@Value无法引入配置文件的数据，由此记录问题+解决方案

<center>
    <img src="/images/posts/blog/java/Java随笔/配置文件数据无法引入01.png.png" alt="picture not found" style="zoom:80%;" />
    <br>
</center>

<center>
    <img src="/images/posts/blog/java/Java随笔/配置文件数据无法引入02.png.png" alt="picture not found" style="zoom:80%;" />
    <br>
</center>

**查看了一下，出现类似情况，有以下原因：**

@Value获取不到配置值几种大概情况

- 变量被关键字static修饰
- 类没有使用@Component及其衍生标签修饰
- 在Bean初始化时构造方法中引用被@Value修饰的变量
- @value 在[拦截器](https://so.csdn.net/so/search?q=拦截器&spm=1001.2101.3001.7020)配置中

OK，仔细检查了，以上问题都不存在；

对比自己以前项目引入的方式，发现问题，引入了错误的Value：

```java
// import lombok.Value;  错误的引入
import org.springframework.beans.factory.annotation.Value; // 正确的引入
```



参考链接：

[@Value读不到配置文件_@value注解读取不到配置文件属性-CSDN博客](https://blog.csdn.net/zws4088/article/details/130685199?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-130685199-blog-100772369.235^v43^pc_blog_bottom_relevance_base2&spm=1001.2101.3001.4242.2&utm_relevant_index=4)
