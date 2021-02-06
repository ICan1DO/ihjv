## Unblock

Use the server to build an unlock Netease Cloud Music node.

## Precondition

Server: Ali Cloud Elastic Service

Mirroring system: CentOS 7.6

## Command Code

```
curl -sL https://rpm.nodesource.com/setup_12.x | bash -
yum install nodejs -y
npm install pm2 -g
yum install git
git clone https://github.com.cnpmjs.org/nondanee/UnblockNeteaseMusic.git
cd UnblockNeteaseMusic
pm2 start app.js --name UnblockNeteaseMusic -- -s -e https://music.163.com -o netease qq xiami kugou kuwo -p 8888:8889
pm2 save
pm2 startup
```
## Install Crt

1. Use safari to click [here](https://raw.githubusercontent.com/nondanee/UnblockNeteaseMusic/master/ca.crt) to enter and install the certificate.

2. Please refer to this [document —— Trust manually installed certificate profiles in iOS and iPadOS](https://support.apple.com/en-us/HT204477)

## iOS Proxy Servers

1. Proxy Type: HTTP

2. Server: Your ip

3. Port: 8888

## VPS Firewall Rules

1. Rule Type: TCP

2. Port: 8888/8889

## pm2 Common Commands

1. pm2 stop UnblockNeteaseMusic `# Stop the service`

2. pm2 restart UnblockNeteaseMusic `# restart service`

3. pm2 pull UnblockNeteaseMusic `# Update service to the latest code`

4. pm2 show UnblockNeteaseMusic `# View service parameter information`

5. pm2 log UnblockNeteaseMusic `# View service log`

6. pm2 ls `# View the list of deployed services`

7. pm2 monit `# Monitor service status`

8. pm2 flush `# Clean up all log files`

9. pm2 update `# Update pm2 status`

## More

- [nondanee/UnblockNeteaseMusic](https://github.com/nondanee/UnblockNeteaseMusic)