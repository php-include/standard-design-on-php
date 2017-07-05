# 建议的开发环境配置

## 新建一个VBox虚拟机，VM或者真机都可以
- centos7
## 目录规划：
- /usr/local/webserver/nginx
- /usr/local/webserver/php7
- /usr/local/webserver/script
- /usr/local/webserver/mongodb
- /usr/local/webserver/mariadb
- /data/web
- /data/logs
- - /data/logs/access
 - - /data/logs/mysql
 - - /data/logs/error
-  /data/git
-  /data/temp
## 需要PHP扩展
- igbinary
- mongodb
- phalcon 
- phpiredis
- swoole
## 安装软件
-  hiredis版本v0.13.1
-  mongodb
-  MariaDB
-  php7.1
- nginx
- FastDFS
- Composer
## 站点定义
- 站点放在/data/web中，以域名为文件夹名字。你也可以把站点放在其他任意位置，通过软链到此目录即可。
- /usr/local/webserver/nginx/vhost  和/usr/local/webserver/nginx/rewrite 为两个基本的域名配置目录
## 安装软件的原则
- 站点运行需要的扩展支持，可以使用yum安装。
- 尽量编译安装软件。