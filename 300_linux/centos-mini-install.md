##### 依赖库

```bash
$ yum reinstall openssh-server openssh
$ yum install epel-release
$ yum install dnf
$ dnf install lrzsz tcpdump lvm2 gcc gcc-c++ glibc glibc-devel libffi-devel sqlite-devel bzip2-devel bzip2 readline-devel openssl-devel bzip2-devel

$ dnf install gcc ncurses-devel readline-devel openssl-devel zlib-devel krb5-devel keyutils-libs-devel libcurl-devel sqlite-devel gdbm-devel bzip2-devel libffi-devel

$ yum install vim git tree wget htop supervisor redis nginx net-tools
$ yum install samba


$ dnf install postgresql11-contrib postgresql11-llvmjit postgresql11-odbc postgresql11-plperl postgresql11-pltcl postgresql11-tcl postgresql11 postgresql11-libs postgresql11-libs
$ dnf install postgresql-devel postgresql postgresql-libs

```

```

yum list libpq*
yum list postgresql11*
```



##### 开发工具包

```
1、查看有那些组安装包可用。
yum grouplist | more

2、搜索一下有哪些和 Development 有关。
yum grouplist | grep Development

3、安装Development Tools这个包。
yum groupinstall "Development Tools"
```

##### 系统python升级到 3.7.10

> https://www.jianshu.com/p/e07fc84bb879

```
$ wget https://registry.npmmirror.com/-/binary/python/3.7.10/Python-3.7.10.tgz
$ ./configure 

$ make
$ make install
安装在目录 /usr/local/bin

```

##### docker

##### java

##### redis

##### nginx

##### pipeline

##### go ??

```
go 语言要 这只一个脚本指定python的语言
```

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



##### 

- 描述

  ```
  
  ```

- 解决办法

  ```
  
  ```



##### 

- 描述

  ```
  
  ```

- 解决办法

  ```
  
  ```



##### 

- 描述

  ```
  
  ```

- 解决办法

  ```
  
  ```



# 解决不了的错误

```
sg_py_call.c:1:20: fatal error: Python.h: No such file or directory
 #include <Python.h>
                    ^
compilation terminated.
make[2]: *** [sg_py_call.s] Error 1
```





