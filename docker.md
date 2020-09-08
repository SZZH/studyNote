- 注意事项
  - 当 container 前台没有服务运行，则容器自动退出
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
      - 如何进入容器，`docker run -it image /bin/bash`,，默认 `/bin/bash`可以省略 
      - 推出容器，在容器的 shell 中打 `exit `
      - 宿主机端口映射到容器，`docker run option -p/--publish 宿主机端口:容器服务端口 image command arguments`
    - kill：`docker kill [options] container [container...]`，杀死一个运行中的容器
    - rm：`docker rm [options] container [container...]`，删除容器
      - `docker rm [optionns] $(docker ps -a -q)`，删除所有容器 
    - exec：`docker exec [options] container command arguments`，进入运行中的容器
    - start/stop/restart：`docker start/stop/restart [OPTIONS] CONTAINER [CONTAINER...]`，启动/停止/重启容器
    - inspect：`docker container inspect 容器id`，查看镜像文件详情
    - ps：`docker container ps [option]`，查看当前运行的容器
      - -a，查看所有
      - -l，查看最近
      - -q，只查看 id
    - port：`docker container port 容器id`，查看当前容器的端口映射情况
    - commit：`docker commit -a“作者” -m"注释" container 新镜像名`，将容器提交为镜像
    - cp：`docker cp 容器id:/xxx.txt .`，将容器文件拷到本机
  - miror
    - pull：`docker pull node:latest`，获取镜像
    - images/image ls：`docker images/image ls`查看所有镜像
    - image rmi：`docker image rmi 镜像名/id`，删除镜像
    - inspect：`docker image inspect 镜像id`，查看镜像详情
    - export：`docker export -o 文件名.tar 容器id`，导出容器为文件
    - import：`docker import 文件名.tar`，文件导入为镜像
    - save：`docker save -o 文件名.tar 镜像id`，镜像导出为文件
    - load：`docker load 文件名.tar`，文件导入为镜像
    - tag：`docker tag 镜像名:tag 新镜像名:tag`，创建一个新的 tag 的镜像，用于备份
  - logs，`docker logs 容器id`，查看容器日志 
  - options
    - -i/--interactive，交互式
    - -t/--tty，分配一个伪终端
    - -d/--detach，后台运行
    - -a/--attach list，附加到运行的容器
    - -e/--env，设置容器内部的环境变量
    - -p/--publish，发布映射端口
    - -P，将容器内的所有端口映射到一个本机随机端口

