## 将 CentOS 7.6 默认 Python2.7.5 升级为 Python 3.9.2

### 1. 查看 python 版本

```
python -V
```

`>>> Python 2.7.5`

### 2. 查看软连接指向

```
ls -al /usr/bin/python
```

`>>> /usr/bin/pytthon -> python2`

### 3. 重命名软连接

```
mv /usr/bin/python /usr/bin/python2.7.5
```

### 4. 下载并解压 python

```
wget https://www.python.org/ftp/python/3.9.2/Python-3.9.2.tgz
tar -xf Python-3.9.2.tgz 
```

### 5. 安装python

```
cd Python-3.9.2
./configure
make && make install
```

### 6. 让系统默认使用 Python 3.9.2

```
vim /usr/bin/yum
```

`#!/usr/bin/python` -> `#!/usr/bin/python2.7.5`

```
vim /usr/libexec/urlgrabber-ext-down
```

`#! /usr/bin/python` -> `#! /usr/bin/python2.7.5`

### 7. 建立新的链接

```
rm -rf /usr/bin/python
rm -rf /usr/bin/py
ln -s /usr/local/bin/python3.9  /usr/bin/python
```
### 8. 升级pip

```
pip install --upgrade pip
```

### 9. 验证是否成功

```
python -V
pip -V
```

`>>> Python 3.9.2`

`>>> pip 21.0.1 from /usr/local/lib/python3.9/site-packages/pip (python 3.9)`



### 快速命令

```
cd
mv /usr/bin/python /usr/bin/python2.7.5
wget https://www.python.org/ftp/python/3.9.2/Python-3.9.2.tgz
tar -xf Python-3.9.2.tgz 
cd Python-3.9.2
./configure
make && make install
vim /usr/bin/yum
```

```
vim /usr/libexec/urlgrabber-ext-down
```

```
rm -rf /usr/bin/python
rm -rf /usr/bin/py
ln -s /usr/local/bin/python3.9  /usr/bin/python
pip install --upgrade pip
python -V
pip -V
```
