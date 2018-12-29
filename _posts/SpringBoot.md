---
layout: default
title: SpringBoot 踩坑小计
---

### 环境
* IDEA-U-18.3.2
* SpringBoot 2.1.1.RELEASE
### 目录
* [修改坐标导致的`BeanDefinitionStoreException`](#COORDINAT_BDSE)
---
### 1 {#COORDINAT_BDSE}
  * 异常：`This can also happen if you are @ComponentScanning a springframework package (e.g. if you put a @ComponentScan in the default package by mistake)`
  * 操作 
    * IDEA 使用 Spring initlizer 创建项目
    * 修改`pom.xml`中的`groupId`与`artifactId`
    * 启动测试类，异常出现
  * 关键代码
    * `@SpringBootApplication(scanBasePackages = {"com.shark.spring.controller"})`
    * ``` 
        @RunWith(SpringRunner.class)
        @SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)
        @ContextConfiguration(classes={BootApplication.class})
        ```
  * 解决方法
    * 不修改其`groupId`与`artifactId`
  * 原因：
    * 不详
    * 