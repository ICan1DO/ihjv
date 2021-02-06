## Unblock

Use the server to build an unlock Netease Cloud Music node.

## Precondition

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

### Method I : Only iOS

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -s -o kuwo qq migu -p 8888:8889 -e https://music.163.com
pm2 save
pm2 startup
```

### Method II : Only PC

1. Install...

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum -y install nodejs -y
yum -y install epel-release
yum -y install supervisor
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
command=/usr/bin/node app.js -p 8887
autostart=true
autorestart=true
```

3. Click `esc` and input `:wq` to save and quit

4. Startup Project

```
systemctl start supervisord
systemctl enable supervisord
```

## Install Crt

1. Use safari to click [here](https://raw.githubusercontent.com/nondanee/UnblockNeteaseMusic/master/ca.crt) to enter and install the certificate.

2. Please refer to this [document —— Trust manually installed certificate profiles in iOS and iPadOS](https://support.apple.com/en-us/HT204477)

## iOS Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8888

## NeteaseMusic(PC) Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8887

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8887/8889

## pm2 Common Commands

```
# Stop the service

pm2 stop UnblockNeteaseMusic

# restart service

pm2 restart UnblockNeteaseMusic

# Update service to the latest code

pm2 pull UnblockNeteaseMusic

# View service parameter information

pm2 show UnblockNeteaseMusic

# View service log

pm2 log UnblockNeteaseMusic

# View the list of deployed services

pm2 ls

# Monitor service status

pm2 monit

# Clean up all log files

pm2 flush

# Update pm2 status

pm2 update
```

## More

- [nondanee/UnblockNeteaseMusic](https://github.com/nondanee/UnblockNeteaseMusic)

- [如风 —— UnblockNeteaseMusic 使用方法](https://desperadoj.com/17.html)