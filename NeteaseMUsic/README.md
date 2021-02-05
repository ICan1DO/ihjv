## 搭建解锁网易云灰度歌曲节点

CentOS 7.6

=====================================
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -s -e https://music.163.com -p 8181:8182
pm2 save
pm2 startup
=====================================

## Surge 代理服务器设置
1. 协议: HTTP
2. 服务器地址: 外网ip
3. 端口: 8181

## VPS 防火墙规则设置
1. 类型: TCP
2. 端口: 8181/8182
