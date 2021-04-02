# CentOS 8.0

## python3.6.8 -> python3.8.2

### 下载安装

```
wget https://www.python.org/ftp/python/3.9.2/Python-3.9.2.tgz
tar -xf Python-3.9.2.tgz 
cd Python-3.9.2
./configure --prefix=/usr/local/python3
make && make install
```

### 备份

```
mv /usr/bin/python /usr/bin/python3_6_old.bak
mv /usr/bin/pip /usr/bin/pip3_6_old.bak
```

### 创建软链

```
ln -s /usr/local/python3/bin/python3 /usr/bin/python
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip
```

### 检查结果

```
python -V
pip -V
```