mysql> SELECT user, host FROM mysql.user;
+------------------+----------------------------+  
| user             | host                       |
+------------------+----------------------------+
| root             | %                          |
| root             | desktop-2acffhf.mshome.net |
| debian-sys-maint | localhost                  |
| mysql.infoschema | localhost                  |
| mysql.session    | localhost                  |
| mysql.sys        | localhost                  |
+------------------+----------------------------+
- 注释：mysql.user表是MySQL数据库中存储用户信息和权限的表，其中user列表示用户名，host列表示允许登录的主机名或IP地址

show grants for 'root'@'desktop-2acffhf.mshome.net';
grant all on test.* to 'root'@'desktop-2acffhf.mshome.net';
flush privileges;
drop user 'your_username'@'desktop-2acffhf.mshome.net';
