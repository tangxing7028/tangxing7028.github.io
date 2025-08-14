---
layout: wiki
title: 随笔
categories: 随笔
description: ‘+’号和StringBuilder的区别
keywords: 随笔
---


在idea中发现，字符串拼接的时候，idea推荐使用‘+’号拼接

### “+”连接真的会耗性能吗？
普通的几个字符串拼接成一个字符串，直接使用“+” ，因为教材等原因，当前依旧有许多人拼接字符串时认为使用“+”耗性能1，首选StringBuilder。

但是，从JDK5开始，Java编译器就做了优化，使用“+”拼接字符串，编译器编译后实际就自动优化为使用StringBuilder。

### 性能测试
新建测试类StrDemo，分别创建使用“+”拼接字符串和使用StringBuilder拼接字符串的方法；

并新增Junit测试用例，分别调用拼接字符串1000000次.

```java
     /**
     * 使用+拼接字符串
     */
    public String concatStringByPlus(String prefix, int i) {
        return prefix + "-" + i;
    }
    /**
     * 使用StringBuilder拼接字符串
     */
    public String concatStringByStringBuilder(String prefix, int i) {
        return new StringBuilder().append(prefix).append("-").append(i).toString();
    }
    /**
     * 测试使用+拼接字符串耗时
     */
    @Test
    public void testStringConcatenation01ByPlus() {
        long startTime = System.currentTimeMillis();
        int count = 1000000;
        for (int i = 0; i < count; i++) {
            String str = concatStringByPlus("testStringConcatenation01ByStringBuilder:", i);
        }
        long endTime = System.currentTimeMillis();
        System.out.println("testStringConcatenation01ByPlus，拼接字符串" + count + "次，花费" + (endTime - startTime) + "秒");
    }
    /**
     * 测试使用StringBuilder拼接字符串耗时
     */
    @Test
    public void testStringConcatenation02ByStringBuilder() {
        long startTime = System.currentTimeMillis();
        int count = 1000000;
        for (int i = 0; i < count; i++) {
            String str = concatStringByStringBuilder("testStringConcatenation02ByStringBuilder:", i);
        }
        long endTime = System.currentTimeMillis();
        System.out.println("testStringConcatenation02ByStringBuilder，拼接字符串" + count + "次，花费" + (endTime - startTime) + "秒");
    }
```
执行结果发现，虽然有差异，但是差异极小，考虑到执行了1000000次，每次耗时的差异就更小了，而且程序执行有各种因素影响执行效率，可以认为耗时差不多。

既然执行效率一样，从代码简洁利于阅读考虑，Idea推荐我们使用“+”拼接字符串就合情合理了。

循环拼接字符串时，尽管使用 "+" 符号进行字符串连接在编译过程中会被优化为使用 StringBuilder，
但每次循环迭代中都会创建一个新的 StringBuilder 对象，这会导致性能上的显著降低。

相比之下，直接使用 StringBuilder 进行操作可以在初始化时仅创建一次对象，从而在整个循环过程中复用，显著提高了效率。
所以大家在大批量循环拼接字符串的情况下，切记不要使用“+”号拼接了

## 总结

1.单纯的字符串拼接使用“+”，更快更简洁。

2.循环拼接时使用“+”拼接字符串效率较低，推荐使用StringBuilder。