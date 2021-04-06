## Unblock by Docker

Use the server to build an unlock Netease Cloud Music node by Docker.

## Server Configuration

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

### 1. Ready For Unblock

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
sudo sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
sudo yum makecache fast
sudo yum install docker-ce
service docker start
docker pull nondanee/unblockneteasemusic
```

### 2. Create a Container

```
docker run -d -p 8083:8080 --name unblockneteasemusic_ios --restart always nondanee/unblockneteasemusic -o kuwo qq migu
docker ps
```

## NeteaseCloudMusic(PC) Server Setting

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8083

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8083
