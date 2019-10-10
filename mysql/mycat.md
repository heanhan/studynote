# Getting Started

### springboot+mycat 使用 Documentation
mycat 的官网地址： http://www.mycat.io/ :

##### 关于mycat

    什么事mycat
        1、一个彻底开源的、面向企业应用开发的大数据库集群
        2、支持事务ACID，可替代Mysql的加强版数据库中间件。
        3、一个可以视为mysql的集群企业级的数据库，用来替代昂贵的oracle数据库。


    为何要使用mycat
        1、支持mysql、Oracle 、DB2、SQL Server、PostgresSQL等常见的DB 数据库。
        2、遵循mysql的原生协议，跨语言的、跨平台、跨数据库，的通用中间件。
        3、基于心跳的自动故障切换，支持读写分离，支持mysql的主从，以及galera cluster 集群。
        4、基于NIO ，有效线程，解决高并发问题。
        5、支持数据的多片的自动路由与聚合，
        6、支持数据的多片自动路由与聚合，支持sum,count,max等常用的聚合函数,支持跨库分页。
        7、支持单库内部任意join，支持跨库2表join，甚至基于caltlet的多表join。
        8、支持通过全局表，ER关系的分片策略，实现了高效的多表join查询。
        9、支持多租户方案。
        10、支持分布式事务（弱xa）。
        11、支持XA分布式事务（1.6.5）。
        12、支持全局序列号，解决分布式下的主键生成问题。
        13、分片规则丰富，插件化开发，易于扩展。
        14、强大的web，命令行监控。


centos7安装下载mycat

        #下载：
        wget http://dl.mycat.io/1.6-RELEASE/Mycat-server-1.6-RELEASE-20161028204710-linux.tar.gz
        #解压
        tar -zxvf Mycat-server-1.6-RELEASE-20161028204710-linux.tar.gz
        #授权
        chmod -R 777 mycat
        #环境变量添加：
        vi /etc/profile
        #在里面添加：
        export MYCAT_HOME=/crawler/mycat/mycat   ##自己的安装路径
        export PATH=$PATH:$MYCAT_HOME/bin
        #使环境变量生效
        source /etc/profile
        #注意：
        #Linux 下部署安装 MySQL，默认不忽略表名大小写，需要手动到/etc/my.cnf 下配置：
        lower_case_table_names=1

使用mycat 的读写分离、分库分表  ，需要的前提： mysql 已经做好了主从分离。

mysql 主从分离

      1、修改主数据库mysql配置,找到主数据库的配置文件 my.cnf（或者my.ini）,在该配置文件中插入下面两行
      [mysqld]
      log-bin=mysql-bin #开启二进制日志
      server-id=1 #设置server-id



配置mycat
