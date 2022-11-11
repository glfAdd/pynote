##### 依赖库

```bash
$ yum reinstall openssh-server openssh
$ yum install epel-release
$ yum install dnf
$ yum install lrzsz tcpdump lvm2 gcc gcc-c++ glibc glibc-devel libffi-devel sqlite-devel bzip2-devel bzip2 readline-devel openssl-devel bzip2-devel

$ yum install gcc ncurses-devel readline-devel openssl-devel zlib-devel krb5-devel keyutils-libs-devel libcurl-devel sqlite-devel gdbm-devel bzip2-devel libffi-devel

$ yum install vim git tree wget htop supervisor redis nginx net-tools
$ yum install samba


$ yum install postgresql11-contrib postgresql11-llvmjit postgresql11-odbc postgresql11-plperl postgresql11-pltcl postgresql11-tcl postgresql11 postgresql11-libs postgresql11-libs
$ yum install postgresql-devel postgresql postgresql-libs

```

```
yum list libpq*
yum list postgresql11*
```

##### 系统python升级到 3.7.1

```
可以不升级, 用 pyenv 安装虚拟环境, 将 pgkconfig 的环境变量指向 python3.pc 路径也可以
```

##### docker

##### java

##### redis

##### nginx

##### pipeline

```
 sh /sdwan/script/run-pipelinedb.sh start
```



##### go 

##### pgkconfig 文件指定

##### 编译成功

```
Compiling './zk_log/zk_log.py'...
Compiling './zk_log/zk_statistics_format.py'...
make[1]: Leaving directory `/root/source/Aquila/build/py-service'
make[1]: Entering directory `/root/source/Aquila/build/oem'
make[2]: Entering directory `/root/source/Aquila/build/oem/qianxin'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/source/Aquila/build/oem/qianxin'
make[2]: Entering directory `/root/source/Aquila/build/oem/report_webui'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/source/Aquila/build/oem/report_webui'
make[1]: Leaving directory `/root/source/Aquila/build/oem'
[root@CTL build]# 
```

##### pg

```
PGPASSWORD
export PGPASSWORD='sdwan#2018'
export ROOTDIR="/media/data"


psql -U  postgres -p 5432 -h 127.0.0.1


先 init 再 check
```

```
check 失败


BINDIR=$(/usr/local/pipelinedb/bin/pg_config --bindir)


yum 安装的 pg 覆盖了以前的路径, 做一次软连接
ln -s /usr/lib/pipelinedb/bin/pg_isready /usr/bin/pg_isready



init 命令不再使用了
```



##### 关闭防火墙

```
systemctl disable firewalld
systemctl stop firewalld
```

## 问题

##### 问题1

- 描述

  ```
  /bin/ld: cannot find -lsqlite3
  collect2: error: ld returned 1 exit status
  make[2]: *** [libsg_db.so] Error 1
  ```

- 解决办法

  ```bash
  $ dnf install sqlite-devel
  ```

##### 问题2

- 描述

  ```
  sg_py_call.c:1:20: fatal error: Python.h: No such file or directory
   #include <Python.h>
  ```

- 解决办法 (不能安装这个)

  ```
  # python2
  $ dnf install python-devel 
  
  # python3
  $ dnf install python3-devel
  ```

##### 问题3

- 描述

  ```
  sg_postgresql.c:4:22: fatal error: libpq-fe.h: No such file or directory
   #include <libpq-fe.h>
  ```

- 解决办法

  ```bash
  $ dnf install postgresql-devel
  ```

##### 问题4

- 描述

  ```
  sg_postgresql.c:4:22: fatal error: libpq-fe.h: No such file or directory
   #include <libpq-fe.h>
  ```

- 解决办法

  ```bash
  $ dnf install postgresql-devel postgresql postgresql-libs
  ```

##### 问题5

- 描述

  ```
  /bin/ld: cannot find -lsg_ssl
  collect2: error: ld returned 1 exit status
  make[2]: *** [libfm.so] Error 1
  ```

- 解决办法

  ```
  dnf install libinput-devel mesa-libgbm-devel libfm  sg3_utils
  
  dnf install libevent libevent-devel
  ```



##### 问题6

```
sh run-postgres.sh check 失败提示
docker does not exist, skip !!!


原因:
脚本问题, 必须设置卡机启动才可以正常运行

(其他脚本可能也存在这个问题)
systemctl enable nginx
systemctl enable redis


```



##### 启动失败

```
需要运行
sh src/script/run.sh start
```



```
ln -s /usr/lib/pipelinedb/bin/pg_isready /usr/bin/pg_isready


pg_config

mkdir /media/sys /media/config /media/data /media/sig /media/stats /media/store 
ln -s /media/sys /sdwan
ln -s /media/config /sdwan/config

```



```
终止home文件进程（切换到非home路径下执行这个命令）：fuser -km /home

        3.1、如果没有fuser，在线安装

               3.1.1、yum安装： yum install -y psmisc

                3.1.2、终止home文件进程（切换到非home路径下执行这个命令）：fuser -km /home

        3.2、如果没有fuser，离线安装

                    3.2.1、下砸地址：https://developer.aliyun.com/packageSearch?word=psmisc

                    3.2.2、下载对应架构离线包（lscpu看centos架构）：

https://blog.csdn.net/u011627218/article/details/121994098

```

##### vmware 扩容

> 成功 https://www.cnblogs.com/friendwang1001/p/15725732.html

> 记录下面的命令
>
> https://blog.csdn.net/monkeyzh123/article/details/117779216
>
> https://blog.csdn.net/lc1183759671/article/details/125601925

```
在创建之后, 用 t 设置格式的时候, 要扩展什么类型, 新建的就选则什么类型


/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    48250879    23075840   8e  Linux LVM
/dev/sda3        48250880   629145599   290447360   8e  Linux LVM
/dev/sda4       629145600   692060159    31457280   83  Linux

扩展 sda1 就创建 Linux 类型
扩展 sda2 就创建 Linux LVM 类型
否则出错




扩展文件系统时
先查看文件系统格式 (这里查看的是 /dev/mapper/centos-root 的)
	cat /etc/fstab | grep centos-root
	
如果是 xfs 用 
	xfs_growfs /dev/mapper/centos-root
如果是 ext2 ext3 ext4 文件系统用
	resize2fs /dev/mapper/centos-root

```

##### pip 安装报错

```
ModuleNotFoundError: No module named '_ctypes'

安装 python 全需要安装
$ yum install libffi-devel
```

##### 启动zk报错

```
kafka-run-class.sh: line 306: exec: java: not found


ln -s /usr/java/jdk-11.0.1/bin/java /usr/bin/java
```

##### python 启动错误

```
nohup: failed to run command ‘venv/bin/python’: Permission denied


原因 /sdwan/py-server 下面 venv/bin 里面的 python 没有可执行权限
```

```
执行 
/sdwan/script/prepare.sh 生成 /sdwan/py-service/public_config/cfg.json 文件
将这个文件拷贝到 代码下的 public_config/cfg.json 中


docker 连接时使用 172.17.0.2 不是 127.0.0.1
```

- 启动时会报很多错

  ```
  设置 /sdwan 的权限 777
  ```

##### sdwan/script/run.sh 问题

```
所有环境刚刚安装好时执行 sh run.sh start 
以后执行 sh run.sh restart
```

##### 日志路径

```
/sdwan/debug/site.log
```

##### 请求卡死

```
运行到 state, src_ip, peer_ip = ext.get_ha_config() 时卡死

调用封装的 .so 库时不同用户没有权限

让 pycharm 启动时用使用 sudo 权限的 python 启动项目
https://zhuanlan.zhihu.com/p/296715567
```

##### 添加设备后无法上线

```
租户许可过期


cpe调试命令
    cpe4> debug sdwan-agent 
    cpe4> debug to terminal 
1. 项目运行 Aquila/src/py-service/mgt_portal/ 目录下创建 media 临时存储文件

2. 登陆 https://https://10.48.112.88/ 创建许可
ctl许可生产 -> 运营许可 -> 导出 license
	机器序列号: 只用运营管理员登陆 -> 账号 -> 关于 -> 软件序列号
	客户名称: 租户的名称
	
3. 运营管理员登陆管控 -> 运维 -> 许可管理 -> 运营许可 -> 导入
```


