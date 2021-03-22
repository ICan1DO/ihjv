## Unblock by pm2

Use the server to build an unlock Netease Cloud Music node by pm2.

## Server Configuration

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -o kuwo qq migu -p 8884:8084
pm2 save && pm2 startup && pm2 log UnblockNeteaseMusic
```

## NeteaseMusic(PC) Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8884

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8884
