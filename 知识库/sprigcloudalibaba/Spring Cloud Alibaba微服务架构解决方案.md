Spring Cloud Alibaba微服务架构解决方案
===
异步非阻塞通信
Netty--->NIO、AIO模型
HTTP--->应用层，可以跨防火墙，在不同的局域网之间通信
RPC---->远程过程调用，TCP通信，在第四层，传输层，优点：速度快，缺点：不能跨防火墙，仅支持局域网通信。
对内RPC、对外restfull。