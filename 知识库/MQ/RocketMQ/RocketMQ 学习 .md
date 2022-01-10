### 一、RocketMQ 的介绍

```
消息队列 是一种先进先出的数据结构。

应用的场景：应用解偶、异步削峰

RabbitMQ：小规模场景，吞吐量低，性能高，功能全面，erlang语言不好控制；
kafka：吞吐量大，会丢失数据，日志分析，大数据采集；
RocketMQ：兼具了上面两种的优点
```

### 二、概念模型

**Producer**：消息生产者，负责生产消息，一般由业务系统负责产生消息。

**Consumer**：消息消费者，负责消费消息，一般是后台系统负责异步消费。

**Push Consumer**：Consumer的一种，需要向Consumer对象注册监听。

**Pull Consumer**：Consumer的一种，需要主动请求Broker拉取消息。

**Producer Group**：生产者集合，一般用于发送一类消息。

**Consumer Group**：消费者集合，一般用于接收一类消息进行消费。

**Broker**：MQ消息服务（中转角色，用于消息存储于生产消息转发）。



### 三、结合 springboot 使用 RocketMQ  

技术背景：基于 JDK 8  springboot +RcoketMQ4.7+mysql +druid ，完成对消息的生产、消费以及防丢失。

1.环境的搭建

pom 坐标的引入

```xml
<dependencies>
        <!--   web容器去掉內嵌的tomcat使用jetty     -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-tomcat</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <!-- 引入jetty容器 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-jetty</artifactId>
            <scope>provided</scope>
        </dependency>

        <!-- 條用工具類的jar 包       -->
        <dependency>
            <groupId>com.example</groupId>
            <artifactId>common-utils</artifactId>
            <version>0.0.1-SNAPSHOT</version>
        </dependency>

        <!--RocketMQ的坐标 是基于 rocketMq 4.6.0 版本-->
        <dependency>
            <groupId>org.apache.rocketmq</groupId>
            <artifactId>rocketmq-spring-boot-starter</artifactId>
            <version>2.1.0</version>
        </dependency>

    </dependencies>
```

