## How To Install Python3

### Install the corresponding compilation tools

```
yum -y groupinstall "Development tools"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
yum install -y libffi-devel zlib1g-dev
yum install zlib* -y
```

### Start to download the installation package and unzip

```
wget https://www.python.org/ftp/python/3.7.2/Python-3.7.2.tar.xz
tar -xvJf  Python-3.7.2.tar.xz
```

### Enter the folder and start the installation (it takes a long time)

```
cd Python-3.7.2
./configure --prefix=/usr/local/python3 --enable-optimizations --with-ssl
make && make install
```

### Create soft connection

```
cd /usr/local/python3
ln -s /usr/local/python3/bin/python3 /usr/local/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/local/bin/pip3
```

## From

- [cnblogs](https://www.cnblogs.com/xiujin/p/11477419.html)
