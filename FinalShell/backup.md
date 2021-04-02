1. 安装 docker 服务

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
sudo sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
sudo yum makecache fast
sudo yum install docker-ce
```

2. 京东 容器1 v4

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

3. 京东 容器2 v4

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

4. 网易云节点

国内服务器 ios

```
docker run -d -p 2020:8080 --name music_ios --restart always nondanee/unblockneteasemusic -s -o kuwo qq migu -e https://music.163.com
```

国内服务器 pc 

```
docker run -d -p 2021:8080 --name music_ios --restart always nondanee/unblockneteasemusic -o kuwo qq migu
```

国外服务器 iOS

```
docker run -d -p 2020:8080 --name music --restart always nondanee/unblockneteasemusic -s -o kuwo joox -e https://music.163.com
```

5. 人形Bot

```
wget https://raw.githubusercontent.com/Xtao-Labs/PagerMaid-Modify/master/utils/docker.sh -O docker.sh&& chmod +x docker.sh && bash docker.sh
```