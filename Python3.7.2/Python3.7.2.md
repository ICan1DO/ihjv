## 一、安装 Python3 (参考自：[博客](https://www.cnblogs.com/xiujin/p/11477419.html))

### 安装相应的编译工具

```
yum -y groupinstall "Development tools"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
yum install -y libffi-devel zlib1g-dev
yum install zlib* -y
```

### 开始下载安装包并解压

```
wget https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
tar -xvJf  Python-3.7.2.tar.xz
```

### 进入文件夹内并开始安装(耗时较长)

```
cd Python-3.7.2
./configure --prefix=/usr/local/python3 --enable-optimizations --with-ssl
make && make install
```

### 创建编译安装目录

```
cd /usr/local/python3
```

### 创建软连接

```
ln -s /usr/local/python3/bin/python3 /usr/local/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/local/bin/pip3
```

### 测试 Python3 是否安装成功

```
python3 -V
pip3 -V
```

- 控制台中输出 `Type "help" ...... ` 则视为成功

- 按 ctrl + z 可退出 Python3
