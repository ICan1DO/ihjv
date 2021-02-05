## UnblockNeteaseMusic

Use the server to build an unlock Netease Cloud Music node.

## Precondition

Mirroring system: CentOS 7.6

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -s -e https://music.163.com -p 8181:8182
pm2 save
pm2 startup
```

## Surge Proxy Servers

1. Proxy Type: HTTP

2. Server: Your ip

3. Port: 8181

## VPS Firewall Rules

1. Type: TCP

2. Port: 8181/8182
