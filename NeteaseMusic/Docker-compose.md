## Unblock by Docker

Use the server to build an unlock Netease Cloud Music node.

## ⚠️ IMPORTANT ⚠️

The UnblockNeteaseMusic's PC or Andriod node built by Docker cannot enable **strict** mode!

So I don't recommend **sharing** this node with anyone.

However, if your device is iOS or Mac, it cloud enable **strict** mode.

## Server Configuration

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
sudo sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
sudo yum makecache fast
sudo yum install docker-ce
service docker start
docker pull nondanee/unblockneteasemusic
```

### 1. If PC

```
docker run -d -p 2020:8080 --name unblockneteasemusicmusic_ios --restart always nondanee/unblockneteasemusic
```

### 2. If iOS/Mac

```
docker run -d -p 2021:8080 --name unblockneteasemusicmusic_ios --restart always nondanee/unblockneteasemusic -s -e https://music.163.com
```

## NeteaseMusic Proxy Servers

### 1. PC

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 2020

### 2. iOS/Mac

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 2021

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 2020/2021
