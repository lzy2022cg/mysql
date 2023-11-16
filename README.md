在WSL中输入ip addr show eth0命令，该命令会返回WSL的IP地址(inet 172.18.150.24，地址在inet后)，将该IP地址作为bind-address的值，这样MySQL就会监听来自该IP地址的连接请求。
cd /etc/mysql/mysql.conf.d/; vim mysqld.cnf; 修改bind-address

mysql> SELECT user, host FROM mysql.user;  
+------------------+----------------------------+  
| user             | host                       |  
+------------------+----------------------------+  
| root             | desktop-2acffhf.mshome.net |  
| debian-sys-maint | localhost                  |  
| mysql.infoschema | localhost                  |  
| mysql.session    | localhost                  |  
| mysql.sys        | localhost                  |  
+------------------+----------------------------+  
- 注释：mysql.user表是MySQL数据库中存储用户信息和权限的表，其中user列表示用户名，host列表示允许登录的主机名或IP地址，.mshome.net是这个域名是一个默认的标识符，用于在本地网络中识别和连接计算机，desktop-2acffhf是主机名在WSL中输入hostname即可显示出来

CREATE USER 'root'@'desktop-2acffhf.mshome.net' IDENTIFIED BY 'your_password';

show grants for 'root'@'desktop-2acffhf.mshome.net';
- 注释：用于查看root用户在desktop-2acffhf.mshome.net主机上的权限。只有当您以root用户和正确的密码登录到desktop-2acffhf.mshome.net主机上时，才能执行这个语句。

GRANT ALL PRIVILEGES ON *.* TO 'root'@'desktop-2acffhf.mshome.net';
- 注释：允许用户 'root' 从指定的主机名访问MySQL服务器上的所有数据库。

flush privileges;
- 注释：主要作用是重新加载系统权限表，并使一些语句立即生效。
  
drop user 'your_username'@'desktop-2acffhf.mshome.net';
