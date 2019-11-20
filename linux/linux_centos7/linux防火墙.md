linux防火墙
===

当前操作基于 red hat/Centos7

	1、查看防火墙状态
		systemctl status firewalld
		service iptables status 
	2、暂时关闭防火墙
		systemctl stop firewwalld
		service iptables stop （关闭防火墙(即时生效，重启后失效)）
	3、永久关闭防火墙
		systemctl disable firewalld
		chkconfig iptables off （关闭防火墙(重启后永久生效)）
	4、重启防火墙
		systemctl enable firewalld
		service iptables restart （开启防火墙(即时生效，重启后失效)
	5、永久关闭后重启
		chkconfigiiptables on

开放防火墙的端口

	1、centos 6 的方式
	

