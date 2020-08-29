- 修改 docker 配置

```JSON
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://xxxxxx.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```

- docker 命令，[参考地址](https://www.runoob.com/docker/docker-run-command.html)
  - container
    - create：`docker create [options] image command arguments`，创建一个容器但不启动
    - run：`docker run [options] image command arguments`，创建容器并运行一个命令
      - 如何进入容器，`docker run -it image /bin/bash`
      - 推出容器，在容器的 shell 中打 `exit `
      - 宿主机端口映射到容器，`docker run option -p 宿主机端口:容器服务端口 image command arguments`
    - kill：`docker kill [options] container [container...]`，杀死一个运行中的容器
    - rm：`docker rm [options] container [container...]`，删除容器
    - exec：`docker exec [options] container command arguments`，在运行的容器中执行命令
    - start/stop/restart：`docker start/stop/restart [OPTIONS] CONTAINER [CONTAINER...]`，启动/停止/重启容器
    - inspect：`docker container inspect 容器id`，查看镜像文件详情
    - ps：`docker container ps [option]`，查看当前运行的容器
      - -a，查看所有
      - -l，查看最近 
    - port，`docker container port 容器id`，查看当前容器的端口映射情况
  - miror
    - pull：`docker pull node:latest`，获取镜像
    - images/image ls：`docker images/image ls`查看所有镜像
    - image rmi：`docker image rmi 镜像名/id`，删除镜像
    - inspect：`docker image inspect 镜像id`，查看镜像详情
  - logs，`docker logs 容器id`，查看容器日志 

