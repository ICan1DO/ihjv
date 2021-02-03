## 基本命令查询

此笔记中的容器名为 jd 或者 jd2

### 查看所有容器情况

`docker ps -a`

- 服务器输出的表格中的 `NAMES` 下面即为容器名

### 启动 Docker 服务

`service docker start`

### 产看创建日志

`docker logs -f 容器名`

### 启动、停止、杀死、删除容器

```
docker start 容器名
docker stop 容器名
docker kill 容器名
docker rm -f 容器名
```

### 重置控制面板用户名和密码

`docker exec -it 容器名 bash jd resetpwd`

### 手动拉取脚本

`docker exec -it 容器名 bash git_pull`

### 手动执行脚本

- 延迟 RandomDelay 秒后执行脚本, RandomDelay 在 config.sh 中设置

`docker exec -it 容器名 bash jd.sh 脚本名(不带.js)`

- 立即执行脚本

`docker exec -it 容器名 bash jd.sh 脚本名(不带.js) now`

### 进入容器查看挂机日志

`docker exec -it 容器名 /bin/bash`

然后

`pm2 monit`

退出

`exit`

