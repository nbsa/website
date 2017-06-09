---
layout: default_cn
title: 快速入门
isDoc: true
docPage: quickstart
displayName: quickstart
icon: home
---

# 第一个Bldae程序

迫不及待要开始了吗？本页提供了一个很好的 Blade `Hello World` 介绍。

## 开发启程

创建一个 maven 工程，加入 Blade 依赖：

![](https://ooo.0o0.ooo/2016/09/07/57cf914bc1eb3.png)

![](https://ooo.0o0.ooo/2016/09/07/57cf91670569f.png)

![](https://ooo.0o0.ooo/2016/09/07/57cf91702328c.png)

```xml
<dependency>
    <groupId>com.bladejava</groupId>
    <artifactId>blade-mvc</artifactId>
    <version>2.0.0-SNAPSHOT</version>
</dependency>
```

创建启动类：

```java
package com.xxx.first;

import com.blade.Blade;

public class Application {
	
    public static void main(String[] args) {
        Blade.of()
        .get("/", (request, response) -> response.html("<h1>Hello Blade</h1>"))
        .start(Application.class, args);
    }
	
}
```

配置一下 `jdk8`，因为我们使用了 `maven` ，默认的编译版本是8以下，所以可以在`pom.xml`加入以下配置指定编译版本：

```xml
<properties>
  <maven.compiler.source>1.8</maven.compiler.source>
  <maven.compiler.target>1.8</maven.compiler.target>
  <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
</properties>
```

也有其他方法可以设置，点[这里](http://www.blogjava.net/fancydeepin/archive/2015/06/23/maven-jdk.html)看看

ok，现在启动 `Application` 的main函数你将看:

```bash
2017-06-09 23:39:23:156 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | Environment: jdk.version		=> 1.8.0_101
2017-06-09 23:39:23:163 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | Environment: user.dir			=> /Users/biezhi/workspace/projects/java/blade
2017-06-09 23:39:23:163 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | Environment: java.io.tmpdir		=> /var/folders/y7/fdpr6jzx1rs6x0jmty2h6lvw0000gn/T/
2017-06-09 23:39:23:164 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | Environment: user.timezone		=> Asia/Shanghai
2017-06-09 23:39:23:164 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | Environment: file.encoding		=> UTF-8
2017-06-09 23:39:23:168 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | Environment: classpath			=> /Users/biezhi/workspace/projects/java/blade/target/test-classes/

							    __, _,   _, __, __,
							    |_) |   /_\ | \ |_
							    |_) | , | | |_/ |
							    ~   ~~~ ~ ~ ~   ~~~
							    :: Blade :: (v2.0.0-SNAPSHOT) 

2017-06-09 23:39:23:198 INFO - [ _(:3」∠)_ ] c.b.m.r.RouteMatcher      | Add route => GET	/hello
2017-06-09 23:39:23:204 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | ⬢ Register bean: [com.blade.Environment@12503e32]
2017-06-09 23:39:23:629 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | ⬢ Blade initialize successfully, Time elapsed: 496 ms
2017-06-09 23:39:23:629 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | ⬢ Blade start with 0.0.0.0:9000
2017-06-09 23:39:23:630 INFO - [ _(:3」∠)_ ] c.b.s.n.NettyServer       | ⬢ Open your web browser and navigate to http://127.0.0.1:9000 ⚡
```

打开浏览器，输入 [http://127.0.0.1:9000](http://127.0.0.1:9000)

wow~ 看起来还不错，这就算走进 Blade 的大门了。


## 都做了什么？

1. 首先，我们创建了 `Application` 类。这个类的是整个程序启动类，它是程序的入口。
2. 接下来，创建了一个路由，这里使用了java8的lambada表达式。
3. 通过 `Response` 对象渲染html。
4. 启动 `start` 方法

## 了解更多

以上的描述介绍了这个应用的启动，虽然它看起来很简单，但也是一个基本的 Blade 应用，我们要开始一个完整的web项目会有如下的一些疑问：

- start方法为什么要传入 `Application.class` ？
- 创建路由还有什么方式？
- 我想更换日志组件怎么办？
- 我想使用模板引擎？
- 配置文件要写在哪里？
- 如何部署到服务器？

等等一系列的问题，作为框架设计者，已经为大家准备好了，如果你是一个web开发的老手可以看看[这个](https://github.com/otale/tale)项目，当然新手直接晋级也是没关系的，因为它非常简单。

> 在开发的过程中有疑问可以参考源码中的测试用例和API Doc基本就可以搞定一切！
