#### 双主双从配置

双主双从即两台主机分别存在两台从机，每台从机只复制对应的主机，两台主机互为主备。

![image-20201209110533313](/Users/zhaojh0912/Library/Application Support/typora-user-images/image-20201209110533313.png)

- 服务器划分

  | 服务器ip       | 角色    |
  | -------------- | ------- |
  | 192.168.20.130 | Master1 |
  | 192.168.20.131 | Slave1  |
  | 192.168.20.132 | Master2 |
  | 192.168.20.133 | Slave2  |

  