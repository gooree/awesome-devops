# Docker实战

## docker search - 查找镜像
```
docker search redis
```

## docker pull - 安装镜像
```
docker pull redis
```

## docker images - 列出已安装的镜像
```
docker images
```

## docker rmi - 删除镜像
```
docker rmi redis
```
Note:可以指定镜像短ID、镜像长ID、镜像名或者镜像摘要

## docker run - 新建并启动容器
```
docker run -p 6379:6379 -v ~/etc/redis/redis.conf:/etc/redis/redis.conf -d redis redis-server /etc/redis/redis.conf
```
可选参数：
1. -p 将容器端口映射到主机端口
2. -v 将主机目录下挂载到容器目录
3. -d 后台运行容器
4. --name 给容器命名
5. --rm 在容器终止后立即删除（不能与-d同时使用）
6. --link 建立容器连接（不需要对外暴露端口）
7. -m 设置容器使用最大内存
8. -it 分配并使用交互终端
9. -e 设置环境变量

## docker ps - 查看正在运行的容器
```
docker ps
```
可选参数：
1. -a 查看所有docker容器

## docker container ls
功能同上

## docker stop - 停止容器
```
docker stop <容器ID>
```

docker stop $(docker ps -a -q)

## docker kill - 强制杀死容器
```
docker kill <容器ID>
```
## docker start - 启动已停止容器
```
docker start <容器ID>
```

## docker logs - 查看容器日志
```
docker logs <容器ID>
```
可选参数：
1. -f 持续查看日志日志输出

## docker top - 查看容器进程
```
docker top <容器ID>
```

## docker exec - 容器交互
```
docker exec -it <容器ID> /bin/bash
```
可选参数：
1. -d 分离模式(在后台运行)
2. -i 即使没有附加也保持STDIN打开
3. -t 分配一个伪终端

## docker rm - 删除容器
```
docker rm <容器ID>
```

## docker build - 使用Dockerfile构建本地镜像
```
docker build -t redis:1.0.0 ./
```
可选参数：
1. -f 指定Dockerfile文件
2. -t 指定镜像名字及标签

## docker tag - 标记镜像
```
docker tag eureka-server:1.0.0 localhost:5000/eureka-server:1.0.0
```

# docker push - 发布镜像到私有仓库
```
sudo docker push localhost:5000/eureka-server:1.0.0
```

