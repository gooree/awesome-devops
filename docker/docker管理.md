# DockerUI vs. Shipyard vs. Portainer
---

1. DockerUI

```
docker run -d -p 9000:9000 --name dockerui -v /var/run/docker.sock:/var/run/docker.sock abh1nav/dockerui
```

2. Shipyard

```
docker run -d -p 9000:8080 --name shipyard -v /var/run/docker.sock:/var/run/docker.sock shipyard/shipyard server
```

1）安装shipyard

```
cat shipyard-deploy | ACTION=deploy bash
```
PS：参见[shipyard－deploy脚本](https://github.com/gooree/awesome-devops/blob/master/docker/shipyard-deploy)

2）停止运行镜像

```
docker stop shipyard-proxy shipyard-certs shipyard-discovery shipyard-rethinkdb shipyard-swarm-agent shipyard-swarm-manager shipyard-controller
```
  
3）启动运行的镜像

```
docker start shipyard-proxy shipyard-certs shipyard-discovery shipyard-rethinkdb shipyard-swarm-agent shipyard-swarm-manager shipyard-controller
```

4）添加节点

```
cat shipyard-deploy | ACTION=node DISCOVERY=etcd://主服务器IP:4001 bash
```

5）删除shipyard

```
cat shipyard-deploy | ACTION=remove bash
```
PS:在节点机上执行，就会将节点从shipyard管理里踢出

3. Portainer

```
docker run -d -p 9000:9000 --name portainer -v /var/run/docker.sock:/var/run/docker.sock -v ~/data/portainer/:/data portainer/portainer
```