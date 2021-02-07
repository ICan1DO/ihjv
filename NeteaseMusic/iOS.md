## Unblock for iOS

Use the server to build an unlock Netease Cloud Music node for iOS.

## Precondition

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
```

```
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git && cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -s -o kuwo qq migu -p 8888:8889 -e https://music.163.com
pm2 save && pm2 startup && pm2 log UnblockNeteaseMusic
```

## Install Crt

1. Use safari to click [here](https://raw.githubusercontent.com/nondanee/UnblockNeteaseMusic/master/ca.crt) to enter and install the certificate.

2. Please refer to this [document —— Trust manually installed certificate profiles in iOS and iPadOS](https://support.apple.com/en-us/HT204477)

## iOS Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8888

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8888
