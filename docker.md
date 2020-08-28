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

- docker 命令

  - [参考地址](https://www.runoob.com/docker/docker-run-command.html)
  - create：`docker create [options] image command arguments`，创建一个容器但不启动
  - kill：`docker kill [options] container [container...]`，杀死一个运行中的容器
    - -s：向容器发一个信号
  - rm：`docker rm [options] container [container...]`，删除容器

  - run：`docker run [options] image command arguments`，创建容器并运行一个命令
    - -d：后台运行
    - -i：以交互模式运行容器，通常与 -t 一起使用 
    - -t：为容器重新分配一个伪输入终端，通常与 -i 一起使用

  - pull：`docker pull node:latest`，获取镜像
  - exec：`docker exec [options] container command arguments`，在运行的容器中执行命令
    - -d：后台运行
    - -i：交互模式
    - -t：分配伪终端
  - start/stop/restart：`docker start/stop/restart [OPTIONS] CONTAINER [CONTAINER...]`，启动/停止/重启容器

