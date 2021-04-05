## 步骤 1: 安装 Docker

1. 如果你曾经安装过 Docker , 请先卸载

```
sudo yum remove docker docker-common docker-selinux docker-engine
```

2. 安装命令如下

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
sudo sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
sudo yum makecache fast
sudo yum install docker-ce
```

## 步骤 2: 启动 Docker 服务

```
service docker start
```

## 步骤 3: 新建一个容器

复制一下代码并粘贴到终端, 然后回车即可, 以下代码中容器安装位置在 `/docker/`

```
docker run -dit \
-v /docker/jd/config:/jd/config \
-v /docker/jd/log:/jd/log \
-v /docker/jd/own:/jd/own \
-v /docker/jd/scripts:/jd/scripts \
-e ENABLE_HANGUP=true \
-e ENABLE_TG_BOT=true \
--name jd \
--hostname jd \
--restart always \
nevinee/jd:v4-bot
```

## 步骤 4: 拉取更新

复制一下代码并粘贴到终端, 然后回车即可

```
docker exec -it jd jup
```

## 步骤 5: 验证一下

复制一下代码并粘贴到终端, 然后回车即可

```
docker exec -it jd jtask bean_change now
```

- 终端输出 `"请先获取Cookie..."` 则代表成功

## 步骤 6:修改配置文件

1. 先进入 `/config/` 文件夹中

```
cd /docker/jd/config
```

2. 然后修 `config.sh` 文件

```
vi congif.sh
```

- 按 `i` 开始编辑模式, 完成后按 `esc` 并输入 `:wq` 后回车即可

3. 修改 `crontab.list` 文件

```
vi crontab.list
```

- 按 `i` 开始编辑模式, 完成后按 `esc` 并输入 `:wq` 后回车即可

4. 修改 `bot.json` 文件

```
vi bot.json
```

- 按 `i` 开始编辑模式, 完成后按 `esc` 并输入 `:wq` 后回车即可

## 步骤 7: 重启容器并登录 Telegram

1. 重启容器

```
docker restart jd
```

2. 按照英文提示输入手机号和验证码