[docker hub](https://hub.docker.com/)

##### 安装

```bash
$ docker pull centos:centos7.9.2009
$ docker run -it --name=c-dev eeb6ee3f44bd
```

##### 命令

```bash
$ docker exec -it c-dev bash
# 发送文件到docker
$ docker cp my.cnf mysql7:/etc/mysql
# 快照
$ docker commit -a="glfAdd" -m="base" 264fbf246c91 c-dev:v1
    -a：提交的镜像作者
    -c：使用 Dockerfile 指令来创建镜像
    -m：提交时的说明文字
    -p：在 commit 时，将容器暂停。
    
    
docker image ls
docker system info
docker --version
docker-compose --version

```

##### 目录

```

```



##### 配置

```bash
$ yum install epel-release
$ yum update -y
$ yum install neovim git tree wget htop supervisor redis nginx net-tools zsh gcc lvm2 libcurl-devel glibc-devel lrzsz ncurses-devel gdbm-devel libffi-devel krb5-devel glibc zlib-devel bzip2-devel readline-devel gcc-c++ bzip2 tcpdump sqlite-devel openssl-devel keyutils-libs-devel python-3 bison
$ yum reinstall openssh-server openssh
```

##### hostname

```

```



```
pyenv
oh my zsh
go
java
python3
```



##### 防火墙

##### selinux





```

```



