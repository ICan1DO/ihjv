## Unblock by pm2

Use the server to build an unlock Netease Cloud Music node by pm2.

## Server Configuration

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Deployment command

### 1. Ready For Unblock

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -s -o kuwo qq migu -p 8888:8889 -e https://music.163.com
pm2 save && pm2 startup && pm2 log UnblockNeteaseMusic
```

### 2. Install Crt

1. Use safari to click [here](https://raw.githubusercontent.com/nondanee/UnblockNeteaseMusic/master/ca.crt) to enter and install the certificate.

2. Please refer to this [document —— Trust manually installed certificate profiles in iOS and iPadOS](https://support.apple.com/en-us/HT204477)

## iOS Proxy Rules

### 1. Remote URL

- [Quantumult X](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/QuantumultX/NetEaseMusic/NetEaseMusic.list)

- [Loon](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Loon/NetEaseMusic/NetEaseMusic.list)

- [Surge](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Surge/NetEaseMusic/NetEaseMusic.list)

- [Shadowrocket](https://raw.githubusercontent.com/blackmatrix7/ios_rule_script/master/rule/Shadowrocket/NetEaseMusic/NetEaseMusic.list)

### 2. Local Rules

```
USER-AGENT,NeteaseMusic*
HOST,apm.music.163.com
HOST,apm3.music.163.com
HOST,interface.music.163.com
HOST,interface3.music.163.com
HOST,music.126.net
HOST,music.163.com
IP-CIDR,101.71.154.241/32
IP-CIDR,103.126.92.132/32
IP-CIDR,103.126.92.133/32
IP-CIDR,112.13.119.17/32
IP-CIDR,112.13.122.1/32
IP-CIDR,115.236.118.33/32
IP-CIDR,115.236.121.1/32
IP-CIDR,118.24.63.156/32
IP-CIDR,193.112.159.225/32
IP-CIDR,223.252.199.66/32
IP-CIDR,223.252.199.67/32
IP-CIDR,39.105.63.80/32
IP-CIDR,45.254.48.1/32
IP-CIDR,47.100.127.239/32
IP-CIDR,59.111.160.195/32
IP-CIDR,59.111.160.197/32
IP-CIDR,59.111.181.35/32
IP-CIDR,59.111.181.38/32
IP-CIDR,59.111.181.60/32
```

## iOS Proxy Servers

1. Proxy Type: HTTP

2. Server: Your VPS ip

3. Port: 8888

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8888
