# 商派ECStore/B2B2c docker

## 说明

这是一个Shopex ECStore B2C/B2B2C docker官方镜像 定制 加强版

*注意*：镜像中只有php 运行环境，不含产品代码包。如需代码，请联系商派（shopex）购买商业授权。www.shopex.cn

欢迎在github上提交PR来改进我们的镜像

## Quick Start - docker-compose 版本

使用docker-compose 一键启动（ 请自行安装 传送门 https://docs.docker.com/compose/install/ ）

*注意*：如果你想使用以下第一种方式，你只需要一个docker-compose.yml文件以及下边对应的一条命令即可

```bash

# 启动php56+mysql+nginx 适用于（Ecstore3.x/B2B2C4.x的ZendGuard加密版本）
# 在启动之前，请先将.env里边的相关变量设置为自己的实际目录 然后找到相应版本的yml目录，执行一下命令
cd ./docker-compose/php56-zendGuard

docker-compose up -d

#如果修改了.env文件中相关设置，请执行以下命令

docker-compose build

docker-compose up -d

#如果想要添加域名访问不同的项目（前提是 都是php72的swoole加密版本）
#请在合适目录下 新建.conf文件 并执行以下命令 （推荐使用对应版本中 conf/nginx-site.conf 的复制文件修改）

docker cp xxx.conf bbc-base:/etc/nginx/conf.d/

docker-compose restart ecstore


# 启动php56+mysql+nginx 适用于（Ecstore5.x的swoole_loader加密版本）
cd ./docker-compose/php56-swooleLoader

docker-compose up -d


# 启动php72+mysql+nginx 适用于（B2B2C5.x的swoole_loader加密版本）
cd ./docker-compose/php72-swooleLoader

docker-compose up -d


```



## Quick Start -Docker 版本(适用于 B2B2C php7.2版本，其它版本请自行修改tag)

```bash


# 启动不含mysql的容器 php7.2-swooleloader 2.0.2
sudo docker run -d -p 8080:80 -v /path-to-ecstore:/data/httpd ecstore/docker-ecstore:php72-swooleloader

# 启动包含mysql的容器 php7.2-swooleloader 2.0.2
sudo docker run -d -p 8080:80 -v /path-to-ecstore:/data/httpd ecstore/docker-ecstore:php72-swooleloader-mysql

# 启动不含mysql的容器 php5.6-swooleloader1.9.0
sudo docker run -d -p 8080:80 -v /path-to-ecstore:/data/httpd ecstore/docker-ecstore:php56-swooleloader-1.9.0

```

### Git repository

The source files for this project can be found here: [https://github.com/wykris/shopex-docker](https://github.com/wykris/shopex-docker)

If you have any improvements please submit a pull request.

### Docker hub repository

The Docker hub build can be found here: [https://hub.docker.com/r/wykrisdev/shopex-docker](https://hub.docker.com/r/wykrisdev/shopex-docker)

## Supported tags and respective Dockerfile links


### 最新版本（官方推荐），适用于 ecstore 5.0 和 b2b2c 5.0版本

*说明：* docker 中默认没有安装 redis server，请自行搭建 redis server.

- [`php72-swooleloader`(*php72-swooleloader/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/master/php72-swooleloader/Dockerfile)
- [`php72-swooleloader-mysql`(*php72-swooleloader-mysql/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/master/php72-swooleloader-mysql/Dockerfile)


| Tag | Nginx | PHP | mysql | ZendGuard Loader | Swoole Loader  | Dockerfile | 适用产品版本 |
|-----|-------|-----|--------|--------| --------|-------- |  ----- |
| php72-swooleloader | nginx/1.12.1 |  7.2.11 | - | - | 2.0.2 |[php72-swooleloader/Dockerfile](https://github.com/wykris/shopex-docker/blob/master/php72-swooleloader/Dockerfile)| b2b2c 5.0 |
| php72-swooleloader-mysql | nginx/1.12.1 |  7.2.11 | 5.6.28 | - | 2.0.2 |[php72-swooleloader-mysql/Dockerfile](https://github.com/wykris/shopex-docker/blob/master/php72-swooleloader-mysqler/Dockerfile)| b2b2c 5.0 |
| php56-swooleloader-2.0.2 | nginx/1.12.1 |  5.6.40 | - | - | 2.0.2 |[php56-swooleloader-2.0.2/Dockerfile](https://github.com/wykris/shopex-docker/blob/master/php56-swooleloader-2.0.2/Dockerfile)| >= ecstore 5.0.2(php5.6)|

### php5.6 - zendgurard
- [`php56-zend`(*php56-zendGuardLoader/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/master/php56-zendGuardLoader/Dockerfile)


### 下面是 swooleloader 1.9.0版本，2018年3月至2018年11月 期间发布的 ecstore5.0.1版本适用此镜像
- [`php56-swooleloader-1.9.0`(*php56-swooleloader/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php56-swooleloader/Dockerfile)
- [`php56-swooleloader-1.9.0-mysql`(*php56-swooleloader-mysql/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php56-swooleloader-mysql/Dockerfile)
- [`php72-swooleloader-1.9.0`(*php72-swooleloader/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php72-swooleloader/Dockerfile)
- [`php72-swooleloader-1.9.0-mysql`(*php72-swooleloader-mysql/Dockerfile*)](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php72-swooleloader-mysql/Dockerfile)

| Tag | Nginx | PHP | mysql | ZendGuard Loader | Swoole Loader  | Dockerfile | 适用产品版本 |
|-----|-------|-----|--------|--------| --------|-------- |  ----- |
| php56-swooleloader-1.9.0 | nginx/1.12.1 |  5.6.37 | - | - | 1.9.0 | [php56-swooleloader/Dockerfile](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php56-swooleloader/Dockerfile)| ECstore B2C 5.0.1|
| php56-swooleloader-1.9.0-mysql | nginx/1.12.1 |  5.6.37 | 5.6.28 | - | 1.9.0 |[php56-swooleloader-mysql/Dockerfile](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php56-swooleloader-mysql/Dockerfile)| ECstore B2C 5.0.1 |
| php72-swooleloader-1.9.0 | nginx/1.12.1 |  7.2.11 | - | - | 1.9.0 |[php72-swooleloader/Dockerfile](https://github.com/wykris/shopex-docker/blob/swooleloader-1.9.0/php72-swooleloader/Dockerfile)| 升级为 swoole 2.0，该版本已弃用 |


相关默认配置：

- `web_root`: /data/httpd/
- `mysql_data`: /data/mysql/
- `php.ini`:/etc/php.ini
- `php-fpm 扩展配置`: /etc/php.d/
- `nginx config`: /etc/nginx/
- `启动脚本`: /start.sh
- `重启 php-fpm`: supervisorctl reload 或 supervisorctl restart all
- `swooleloader 配置`: /etc/php.d/swoole_loader.ini 

## swooleloader 证书配置方法(b2b2c v5.0和 ecstore v5.0请注意检查此配置下）：
vim /etc/php.d/swoole_loader.ini
```bash
[swoole]
extension = swoole_loader72.so
;加入授权证书文件，更改后，需要重启 php-fpm 才能生效
swoole_license_files=/data/httpd/config/developer.zl
```

### mysql info（适用于nginx-php56-mysql56)

**mysql 默认没有密码**

To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:

  /usr/bin/mysqladmin -u root password 'new-password'
  /usr/bin/mysqladmin -u root -h 563dacdc4a71 password 'new-password'

Alternatively you can run:

  /usr/bin/mysql_secure_installation

which will also give you the option of removing the test
databases and anonymous user created by default.  This is
strongly recommended for production servers.

See the manual for more instructions.

You can start the MySQL daemon with:

  cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with mysql-test-run.pl

  cd mysql-test ; perl mysql-test-run.pl

Please report any problems at http://bugs.mysql.com/

The latest information about MySQL is available on the web at  http://www.mysql.com

### php5.6 默认扩展情况(swooleLoader)

```bash
[PHP Modules]
bcmath
bz2
calendar
Core
ctype
curl
date
dom
ereg
exif
fileinfo
filter
ftp
gd
gettext
gmp
hash
iconv
igbinary
json
libxml
mbstring
mcrypt
mhash
mysql
mysqli
mysqlnd
openssl
pcntl
pcre
PDO
pdo_mysql
pdo_sqlite
Phar
posix
readline
redis
Reflection
session
shmop
SimpleXML
sockets
SPL
sqlite3
standard
swoole_loader
sysvmsg
sysvsem
sysvshm
tokenizer
wddx
xml
xmlreader
xmlwriter
xsl
zip
zlib

[Zend Modules]

```

### php5.6 默认扩展情况(zendGuardLoader)

```bash
[PHP Modules]
bcmath
bz2
calendar
Core
ctype
curl
date
ereg
exif
fileinfo
filter
ftp
gd
gettext
gmp
hash
iconv
json
libxml
mbstring
mcrypt
mhash
mysql
mysqli
mysqlnd
openssl
pcntl
pcre
PDO
pdo_mysql
pdo_sqlite
Phar
readline
Reflection
session
shmop
SimpleXML
sockets
SPL
sqlite3
standard
tokenizer
xml
Zend Guard Loader
zip
zlib

[Zend Modules]
Zend Guard Loader

```

### php7.2默认扩展

```bash
[PHP Modules]
bcmath
bz2
calendar
Core
ctype
curl
date
exif
fileinfo
filter
ftp
gd
gettext
gmp
hash
iconv
json
libxml
mbstring
mysqli
mysqlnd
openssl
pcntl
pcre
PDO
pdo_mysql
pdo_sqlite
Phar
readline
Reflection
session
shmop
SimpleXML
sockets
SPL
sqlite3
standard
swoole_loader
tokenizer
xml
zip
zlib

[Zend Modules]

```
