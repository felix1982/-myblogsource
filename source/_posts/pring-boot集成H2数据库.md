title: spring-boot集成H2数据库
tags:
  - h2
  - spring boot
categories:
  - spring boot
author: felix1982
date: 2019-02-21 22:30:00
---
---
在日常开发过程中,特别是敏捷开发过程以及测试过程中,我们有时候不想操纵真实的数据库.那么,H2数据库是个不错的选择。
> H2是一个开源的、纯java实现的关系数据库。
> h2数据库特点
>（1）性能、小巧
>（2）同时支持网络版和嵌入式版本，另外还提供了内存版
>（3）有比较好的兼容性，支持相当标准的sql标准
>（4）提供了非常友好的基于web的数据库管理界面

在spring boot项目中配置H2数据库

**application.properies**
~~~
spring.datasource.url=jdbc:h2:mem:test_db
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.schema=classpath:db/schema.sql
spring.datasource.data=classpath:db/data.sql
spring.h2.console.enabled=true
~~~

* **spring.datasource.url=jdbc:h2:mem:test**，配置h2数据库的连接地址
* **spring.datasource.driver-class-name=org.h2.Driver**，配置JDBC Driver
* **spring.datasource.username=root**，配置数据库用户名
* **spring.datasource.password=**，配置数据库密码
* **spring.datasource.schema=classpath:db/schema.sql**，进行该配置后，每次启动程序，程序都会运行resources/db/schema.sql文件，对数据库的结构进行操作。
* **spring.datasource.data=classpath:db/data.sql**,进行该配置后，每次启动程序，程序都会运行resources/db/data.sql文件，对数据库的数据操作
* spring.h2.console.enabled=true，开启web console功能

**schema.sql**
~~~sql
CREATE TABLE student(
 id int not null,
 name varchar(20) null,
 age int null
);
~~~
**data.sql**
~~~sql
INSERT  INTO  student VALUES (1,'张三',10);
INSERT  INTO  student VALUES (2,'李四',16);
~~~
项目目录结构变为如下:
![image1](/images/1.png)

配置完成后,启动项目后，浏览器中输入http://localhost:8080/h2-console/，显示H2数据的连接页面

![image2](/images/2.png)

登录后页面为:
![image3](/images/3.png)
