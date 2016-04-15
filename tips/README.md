# 那些年踩过的各种坑。。。

* 模板类中静态数据是否共享
* cassandra 一致性等级问题
* java map 线程冲突问题
* i++的问题
* netbeans 启动单元测试起不起来
  * 发现是公司的二方库的问题
  * +- cn.fraudmetrix:module-kafka:jar:1.0.10:compile
[INFO] |  +- org.apache.kafka:kafka_2.10:jar:0.8.2.1:compile
[INFO] |  |  +- com.yammer.metrics:metrics-core:jar:2.2.0:compile
[INFO] |  |  +- org.scala-lang:scala-library:jar:2.10.4:compile
[INFO] |  |  +- org.apache.kafka:kafka-clients:jar:0.8.2.1:compile
[INFO] |  |  |  +- net.jpountz.lz4:lz4:jar:1.2.0:compile
[INFO] |  |  |  \- org.xerial.snappy:snappy-java:jar:1.1.1.6:compile
[INFO] |  |  +- org.apache.zookeeper:zookeeper:jar:3.4.6:compile
[INFO] |  |  |  \- jline:jline:jar:0.9.94:compile
[INFO] |  |  +- net.sf.jopt-simple:jopt-simple:jar:3.2:compile
[INFO] |  |  \- com.101tec:zkclient:jar:0.3:compile
[INFO] |  \- org.testng:testng:jar:6.1.1:compile

  * 这个库里的org.testng似乎与外部的
  * +- junit:junit:jar:4.11:test
[INFO] |  \- org.hamcrest:hamcrest-core:jar:1.3:test
冲突

* jedis连接报错，bean注入失败
  * Could not instantiate bean class [redis.clients.jedis.JedisPool]: Constructor threw exception; nested exception is redis.clients.jedis.exceptions.InvalidURIException: Cannot open Redis connection due invalid URI. 192.168.6.38
  * 排查发现是bean通过构造函数注入，参数类型没有强制指定

