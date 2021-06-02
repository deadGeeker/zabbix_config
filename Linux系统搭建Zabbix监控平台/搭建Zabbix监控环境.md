+ 搭建 Zabbix 监控平台有四个关键：Web 管理界面、服务器，客户端和数据库。
# 服务器与界面
---
+ 安装支持 MySQL 的 Zabbix Server，以及对应的 Web 界面
+ $ sudo apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf
---
# 启动 MySQL
---
+ $ sudo service mysql start
+ 创建数据库和用户
+ 创建一个名叫 zabbix 的数据库，字符集设置为 utf8
+ $ CREATE DATABASE zabbix CHARACTER SET utf8 COLLATE utf8_bin;
+ 切换数据库：
+ USE zabbix;
+ 创建一个用户 zabbix，密码为 zabbixPSWD，用于连接数据库
+ create user zabbix@localhost identified by 'zabbixPSWD';
+ grant all privileges on zabbix.* to zabbix@localhost;
+ 修改 Zabbix Server 的配置
+ 在 zabbix_server.conf 中编辑数据库配置
+ $ sudo vim /etc/zabbix/zabbix_server.conf
+ DBHost=localhost
+ DBName=zabbix
+ DBUser=zabbix
+ DBPassword=zabbixPSWD
+ sudo service zabbix-server start
+ 启动 Zabbix Server
+ sudo service zabbix-server start
---