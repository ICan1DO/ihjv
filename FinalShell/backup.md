### 安装 docker 服务

```
yum install -y yum-utils device-mapper-persistent-data lvm2
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
yum makecache fast
yum install docker-ce
```

### 京东 v4

1. 第一个容器

```
docker run -dit \
-v /docker/jd/config:/jd/config \
-v /docker/jd/log:/jd/log \
-v /docker/jd/scripts:/jd/scripts \
-v /docker/jd/own:/jd/own \
-p 1998:5678 \
-e ENABLE_HANGUP=true \
--name jd \
--hostname jd \
--restart always \
nevinee/jd:v4
```

2. 第二个容器

```
docker run -dit \
-v /docker/jd2/config:/jd/config \
-v /docker/jd2/log:/jd/log \
-v /docker/jd2/scripts:/jd/scripts \
-v /docker/jd2/own:/jd/own \
-p 1999:5678 \
-e ENABLE_HANGUP=true \
--name jd2 \
--hostname jd \
--restart always \
nevinee/jd:v4
```

### 京东 v4-bot

1. 第一个容器

```
docker run -dit \
-v /docker/jd/config:/jd/config \
-v /docker/jd/log:/jd/log \
-v /docker/jd/own:/jd/own \
-v /docker/jd/scripts:/jd/scripts \
-e ENABLE_HANGUP=true \
-e ENABLE_TG_BOT=true \
--name jd \
--hostname jd \
--restart always \
nevinee/jd:v4-bot
```

2. 第二个容器

```
docker run -dit \
-v /docker/jd2/config:/jd/config \
-v /docker/jd2/log:/jd/log \
-v /docker/jd2/own:/jd/own \
-v /docker/jd2/scripts:/jd/scripts \
-e ENABLE_HANGUP=true \
-e ENABLE_TG_BOT=true \
--name jd2 \
--hostname jd \
--restart always \
nevinee/jd:v4-bot
```

3. 机器人命令

```
start - 开始使用本程序
help - 获取帮助
node - 前台执行脚本
cmd - 执行cmd命令
snode - 后台执行脚本
log - 选择查看执行日志
getfile - 获取jd目录下文件
getcookie - 扫码获取cookie
```

### 网易云节点

1. 国内服务器 iOS

```
docker run -d -p 2020:8080 --name music_ios --restart always nondanee/unblockneteasemusic -s -o kuwo qq migu -e https://music.163.com
```

2. 国内服务器 PC 

```
docker run -d -p 2021:8080 --name music_pc --restart always nondanee/unblockneteasemusic -o kuwo qq migu
```

3. 国外服务器 iOS

```
docker run -d -p 2020:8080 --name music --restart always nondanee/unblockneteasemusic -s -o kuwo joox -e https://music.163.com
```

### 人形Bot

```
wget https://raw.githubusercontent.com/Xtao-Labs/PagerMaid-Modify/master/utils/docker.sh -O docker.sh&& chmod +x docker.sh && bash docker.sh
```

### 宝塔面板

1. 安装命令

```
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```

2. 取消登录

```
sed -i "s|if (bind_user == 'True') {|if (bind_user == 'REMOVED') {|g" /www/server/panel/BTPanel/static/js/index.js
```