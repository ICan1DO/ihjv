## Unblock for Windows or Android

Use the server to build an unlock Netease Cloud Music node for Windows or Android.

## Precondition

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

1. Install...

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum -y install nodejs -y
yum -y install epel-release
yum -y install supervisor
```

```
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
vim /etc/supervisord.d/netease.ini
```

2. Input `i` to modify file content

```
[supervisord]
nodaemon=false

[program:netease]
user=root
directory=/root/UnblockNeteaseMusic
command=/usr/bin/node app.js -p 8886
autostart=true
autorestart=true
```

3. Click `esc` and input `:wq` to save and quit

4. Startup Project

```
systemctl start supervisord
systemctl enable supervisord
```

## NeteaseMusic(PC) Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8886

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8886
