# docker compose environment

## 开发部署的docker环境

### 说明

1. docker镜像是自定义的[ifucloud/php-nginx](https://hub.docker.com/r/ifucloud/php-nginx/tags/)

### 使用

1. 服务器安装docker、docker-compose

2. 获取环境并启动环境

```shell
git clone https://github.com/ifucloud/docker-compose-ali28.git

cd docker-compose-ali28

docker-compose up -d
```

3. 增加项目容器

* 在docker-compose.yml 文件中增加一组自己的服务配置，使用`docker-compose up -d`重新构建运行环境

* 在etc/nginx.conf中配置反向代理地址

### 环境架构

1. 使用一个独立的nginx作为转发服务，有共有的mysql和redis，分别映射到了物理机的3306和6379端口

2. 项目代码统一放在/www/code目录中，共有mysql数据文件放在www/data/mysql-data中

3. 每一个项目容器（业务代码运行的容器）应该拥有自己独立解析php的能力（包括nginx或apache，默认为nginx）