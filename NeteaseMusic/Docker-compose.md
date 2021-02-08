## Unblock by Docker-compose

Use the server to build an unlock Netease Cloud Music node.

## ⚠️ IMPORTANT ⚠️

The UnblockNeteaseMusic node built by Docker-compose cannot enable **strict** mode!

So I don't recommend **sharing** this node with anyone.

## Server Configuration

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

```
yum install docker -y
systemctl start docker
systemctl enable docker
yum install python-pip3
pip3 install --upgrade pip3
```

```
pip3 install docker-compose
docker pull nondanee/unblockneteasemusic
docker run --name music -p 8887:8080 nondanee/unblockneteasemusic
docker ps
```

## NeteaseMusic(PC) Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8887

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8887
