##### 问题

```
python3.7m

```

# python

##### 编译安装 pyton

```bash
# 3.7.10 / 3.9.16
$ wget https://registry.npmmirror.com/-/binary/python/3.7.10/Python-3.7.10.tar.xz
$ wget https://registry.npmmirror.com/-/binary/python/3.9.16/Python-3.9.16.tar.xz

$ cd Python-3.7.10
$ ./configure --prefix=/opt/python-3.7.10 --enable-optimizations
$ make
$ make install

$ python3 -m pip install virtualenv
```

##### 删除编译安装 python

```bash
# 1. 搜索安装包
$ rpm -qa|grep python3

# 2. 卸载
$ rpm -e python3-rpm-macros-3-34.el7.noarch
或
$ rpm -e --nodeps python3-rpm-macros-3-34.el7.noarch
    -e: 卸载   
    --nodeps: 忽略依赖
    
# 3. 查看是否都卸载了
$ whereis python3
```

##### 开发工具

```bash
$ yum install python-devel python3-devel
```

##### pip 安装

- centos 8 stream

  ```bash
  $ dnf reinstall python2-pip
  $ dnf reinstall python3-pip
  ```

- centos 7

  ```bash
  $ yum install python-pip
  $ pip install --upgrade pip
  
  
  https://pypi.org/project/pip/
  
  $ wget https://files.pythonhosted.org/packages/a3/50/c4d2727b99052780aad92c7297465af5fe6eec2dbae490aa9763273ffdc1/pip-22.3.1.tar.gz
  
  $ python setup.py install
  ```

#####  pip 安装(2)

- 在 Python2.x 中安装

  ```bash
  $ curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip2.py
  $ sudo python get-pip2.py
  $ pip --version
  $ pip install --upgrade pip
  ```

- 在 Python3.x 中安装

  ```bash
  $ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
  $ sudo python3 get-pip.py
  $ pip3 --version
  $ pip3 install --upgrade pip
  ```

# pip

##### pip 参数

| 参数    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| --user  | 安装第三方库时只对当前用户可见<br />会将程序包安装到 $HOME/.local 路径下, 其中包含三个字文件夹 bin, lib 和 share<br />在虚拟环境下不可使用 --user 选项, 因为用户目录在该环境下不可见 |
| --force |                                                              |

##### 临时改变源

```bash
$ pip install -i https://pypi.tuna.tsinghua.edu.cn/simple -r requirements.txt
```

##### 永久改变源 

```
创建并添加 ~/.pip/pip.conf

[global]
index-url = https://pypi.mirrors.ustc.edu.cn/simple/
[install]
trusted-host = https://pypi.mirrors.ustc.edu.cn/
```

# pyenv

##### 依赖 - centos

```bash
$ dnf install gcc gcc-c++ glibc glibc-devel libffi-devel sqlite-devel bzip2-devel bzip2 readline-devel openssl-devel bzip2-devel make zlib zlib-devel patch lzma xz-devel
```

##### 依赖 - mac

```bash
# 升级系统python
$ brew reinstall python
$ brew install zlib openssl
```

##### 依赖 - ubuntu

```bash
$ apt-get install build-essential zlib1g-dev
```

##### pyenv

> [github](https://github.com/pyenv/pyenv)
>
> pip 包安装在虚拟环境的 ~/.pyenv/versions/p-3.9.2-learn/lib 目录下

- clone

  ```bash
  $ git clone https://github.com/pyenv/pyenv.git ~/.pyenv
  ```

- 设置变量 - zsh

  ```shell
  $ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
  $ echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
  $ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
  ```

##### pyenv-virtualenv

> [github](https://github.com/pyenv/pyenv-virtualenv)
>
> 用于创建 python 虚拟环境

- clone

  ```bash
  $ git clone https://github.com/pyenv/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
  ```
  
- .zshrc 添加如下内容:

  ```bash
  $ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
  ```

```
exec $SHELL -l
```

##### 命令

```bash
pyenv help install
pyenv commands				# 所有可用的 pyenv 命令
pyenv version  				# 显示当前目录下采用的 python 版本
pyenv versions 				# 列出系统中安装的 python 版本
pyenv install --list		# 列出可安装版本
pyenv install <version>		# 安装对应版本 
pyenv install -v <version>	# 安装对应版本，若发生错误，可以显示详细的错误信息 
pyenv uninstall <version>	# 卸载 python 3.4.0
pyenv which python			# 显示当前python安装路径 
pyenv global <version>		# 全局设置, 整个系统生效 
pyenv local <version>		# 当前路径创建一个.python-version, 以后进入这个目录自动切换为该版本 
pyenv shell <version>		# 当前shell的session中启用某版本，优先级高于global 及 local
pyenv rehash 				# 安装完成之后需要对数据库进行更新



pyenv virtualenvs
pyenv virtualenv <version> <name> 	# 创建3.6.4版本的虚拟环境 
pyenv activate <name> 				# 激活 env-3.6.4 这个虚拟环境 
pyenv deactivate 					# 停用当前的虚拟环境 
pyenv uninstall env-3.6.4 			# 删除 env-3.6.4 这个虚拟环境
```

```
# 安装时使用 -v 查看详细信息, 缺少哪个依赖安装哪个
$ pyenv install -v 3.9.2
```



```
pyenv global 3.3.3 2.7.6
pyenv versions
  system
* 2.7.6 (set by /Users/yyuu/.pyenv/version)
* 3.3.3 (set by /Users/yyuu/.pyenv/version)
  venv27
```

##### 离线包安装python

```
阿里源下载 https://registry.npmmirror.com/binary.html?path=python/
    wget https://registry.npmmirror.com/-/binary/python/3.7.10/Python-3.7.10.tar.xz
    wget https://registry.npmmirror.com/-/binary/python/3.9.16/Python-3.9.16.tar.xz

*.tar.xz
创建目录放安装文件 ~/.pyenv/cache
使用 pyenv install 2.7.16 查看下载文件的目录, 并用wget下载
安装 pyenv install 2.7.16
```

# venv

```bash
# venv 模块是 Python3.3 后自带的虚拟环境创建和管理工具, Python2.X不能使用, 因此只能创建 python3 的虚拟环境, 并且是系统已经存在的.
$ python3 -m venv /home/yan/env3
```

# virtualenv

> virtualenv 同时支持 Python2.X 和 Python3.X, 并且是系统已经存在的.

```bash
# 安装
$ pip install virtualenv


# 参数
	--no-site-packages: 已经安装到系统 python 环境中的所有第三方包都不会复制过来
	--system-site-packages: 与上面相反
	--distribute: 
	-p:


# 安装python2.7虚拟环境
$ virtualenv /home/yan/env 
# 安装 python3.5 虚拟环境
$ virtualenv -p /usr/bin/python3.5 --no-site-packages test


# 激活虚拟环境
$ source /home/yan/env3/bin/activate
$ source ./venv/bin/activate
$ source ./venv/Scripts/activate

# 退出环境
$ deactivate 
```

# virtualenvwrapper

> 对 virtualenv 的一个封装
>
> 所有环境保存在 ~/.virtualenvs 
>
> [pip](https://pypi.org/project/virtualenvwrapper/)

##### 安装

- 安装 (依赖 virtualenv)

  ```bash
  $ pip3 install --user virtualenv
  $ pip3 install --user virtualenvwrapper
  ```

-  设置环境变量 (~/.zshrc)

  ```bash
  # 所有的虚拟环境会创建在 WORKON_HOME 目录下
  export WORKON_HOME=$HOME/.virtualenvs
  export PROJECT_HOME=$HOME/workspace
  # 指定 python 路径
  export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
  # 指定 virtualenv 路径
  export VIRTUALENVWRAPPER_VIRTUALENV=~/.local/bin/virtualenv
  ```

- 激活

  ```bash
  $ source ~/.zshrc
  $ source ~/.local/bin/virtualenvwrapper.sh
  ```

##### 环境变量

```bash
# 指定使用 mkproject 创建的项目路径
PROJECT_HOME

# 指定 hooks 目录, 默认 $WORKON_HOME
VIRTUALENVWRAPPER_HOOK_DIR

# hooks 日志
VIRTUALENVWRAPPER_LOG_FILE

# 1 (默认): 使用 mkproject projectname 创建虚拟环境及工程目录后, workon projectname 默认会自动切换项目目录
# 0: workon projectname 不进入工程目录只激活虚拟环境
VIRTUALENVWRAPPER_WORKON_CD

# python 路径
VIRTUALENVWRAPPER_PYTHON

# virtualenv 路径
VIRTUALENVWRAPPER_VIRTUALENV

# 产生的临时文件位置 ( 默认 $TMPDIR, 如果没有使用 /tmp)
VIRTUALENVWRAPPER_TMPDIR
```

##### 命令

```bash
mkvirtualenv [-a project_path] [-i package] [-r requirements_file] [virtualenv options] env_name

# 创建虚拟环境：
$ mkvirtualenv my_venv
$ mkvirtualenv -p /opt/python-3.11.1/bin/python my_venv
# 环境列表
$ workon
# 开始在虚拟环境
$ workon my_venv
# 注销当前已经被激活的虚拟环境：
$ deactivate
# 删除虚拟环境：
$ rmvirtualenv my_venv  
# 退出环境
$ deactivate
# 虚拟环境的列表
$ lsvirtualenv
# 进入当前激活的虚拟环境
$ cdvirtualenv
# 进入虚拟环境中的site-packages目录
$ cdsitepackages
# 列出当前环境安装了的包
$ lssitepackages


mkproject mic：创建mic项目和运行环境mic
mktmpenv：创建临时运行环境
```

# pipenv

```
pip 包管理工具
```

```bash
$ pip3 install --user pipenv
```

```
会在项目目录下生成2个文件Pipfile和Pipfile.lock


pipenv install --dev生成自己的虚拟环境。

Pipfile.lock 文件是通过hash算法将包的名称和版本，及依赖关系生成哈希值，可以保证包的完整性。
```

# 错误 / 失败

##### pip list

- 报错信息

  ```
  DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the [list] section) to disable this warning.
  ```

- 解决办法, 在 .pip/pip.conf 中添加

  ```
  [list]
  format = columns
  ```

##### pyltp 安装

```
error: $MACOSX_DEPLOYMENT_TARGET mismatch: now "10.12" but "10.15" during configure

切换到虚拟环境
$ git clone https://github.com/HIT-SCIR/pyltp
$ cd pyltp
$ git submodule init
$ git submodule update
vim setup.py 修改文件121行
os.environ['MACOSX_DEPLOYMENT_TARGET'] = '10.12'
修改为后问题解决
os.environ['MACOSX_DEPLOYMENT_TARGET'] = '10.14' 
$ python setup.py install


$ MACOSX_DEPLOYMENT_TARGET=10.7 python setup.py install
```

##### 安装 psycopg2

- centos

  ```bash
  $ yum install libjpeg libjpeg-devel zlib zlib-devel freetype freetype-devel lcms lcms-devel
  $ yum install postgresql-devel*
  $ yum install python-imaging
  ```

- mac

  ```bash
  $ brew update
  $ brew install --force ossp-uuid
  $ brew install postgresql
  $ pip install psycopg
  ```



