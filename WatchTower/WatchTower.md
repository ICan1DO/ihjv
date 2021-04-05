## 启动命令

直接在终端中粘贴以下启动命令

```
docker run -d \
--name watchtower \
--restart unless-stopped \
-v /var/run/docker.sock:/var/run/docker.sock \
containrrr/watchtower \
```