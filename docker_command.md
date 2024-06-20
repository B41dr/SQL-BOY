###  docker常用指令

**拉取镜像**

要拉取docker镜像，可以使用以下命令：

```bash
docker pull <image>
```

**查询镜像**

要查询本地所有的镜像，可以使用以下命令：

```bash
docker images
```

**删除镜像**

要删除本地对应的镜像，可以使用以下命令：

```bash
docker rmi <image>
```

**查询容器**

要展示运行中的容器，可以使用以下命令：

```bash
docker ps
```

要展示所有的容器，可以使用以下命令：

```bash
docker ps -a
```

**删除容器**

```bash
docker rm <container>
```

**查看容器资源使用情况**

```bash
docker stats <container>
```

**停止和启动容器**

要停止运行的容器，可以使用以下命令：

```bash
docker stop <container>
```

要启动该容器，可以使用以下命令：

```bash
docker start <container>
```

要重启该容器，可以使用以下命令：

```bash
docker restart <container>
```

**列出数据卷**

```bash
docker volume ls
```

**创建数据卷**

```bash
docker volume create <volume_name>
```

**挂载数据卷到容器**

```bash
docker run -d --name <container> -v <volume_name>:<container_path> <image_name>
```

**删除数据卷**

```bash
docker volume rm <volume_name>
```

**列出网络**

```bash
docker network ls
```

**创建自定义网络**

```bash
docker network create <network_name>
```

**将容器连接到网络**

```bash
docker network connect <network_name> <container>
```

**将容器连接到网络**

```bash
docker network disconnect <network_name> <container>
```