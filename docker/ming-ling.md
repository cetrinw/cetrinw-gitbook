---
description: 一些常用的docker命令
---

# 命令

```json
//加载tar包
docker load -i sfcz-sync.tar.gz  
//构建
docker buildx build  -t sfcz-sync:v0.1 ../docker   
//镜像列表
docker images      
//运行的容器列表
docker ps -a 
//删除容器
docker rm //容器id
//删除镜像
docker rmi //镜像id
```
