# odoo-16


# Docker 构建命令:
```shell
docker build  -f  ./00-Dockerfile-initial  .    -t mengxy32/odoo-16.0:20240126-initial
docker build  -f ./01-Dockerfile-odoo-start  .    -t mengxy32/odoo-16.0:20240126-all-v1.0
```

```
mengxy32/odoo-16.0:20240126-initial 用于安装odoo 初始化的基础镜像。
mengxy32/odoo-16.0:20240126-all-v1.0 为构建好的一个完整的v16版本的odoo 镜像。
```
使用与测试方法：

```
启动数据库
docker run -d -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo -e POSTGRES_DB=postgres --name db postgres:15

测试odoo 编译情况，前台查看日志方式启动
docker run -p 8069:8069 --name odoo --link db:db -t mengxy32/odoo-16.0:20240126-all-v1.0

后台启动
docker run -p 8069:8069 --name odoo --link db:db -d -t mengxy32/odoo-16.0:20240126-all-v1.0

清理镜像与运行的docker 
docker rm -f odoo 

删除数据库 
docker rm -f db
```
