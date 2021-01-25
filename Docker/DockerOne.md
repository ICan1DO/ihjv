## 第一步: 安装 Docker

1. 如果之前安装过 Docker 需要先卸载

`sudo yum remove docker docker-common docker-selinux docker-engine`

2. 安装依赖

`sudo yum install -y yum-utils device-mapper-persistent-data lvm2`

3. 下载 repo 文件(CentOS)

`wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo`

4. 把软件仓库地址替换为 TUNA

`sudo sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo`

5. 最后安装

```
sudo yum makecache fast
sudo yum install docker-ce
```

6. 防后面报错

`npm install got`

## 第二步: 创建容器

复制粘贴回车以下代码, 此中 Docker 的安装位置为 /docker/

- 最后一行推荐使用 `evinedeng/jd:gitee`, 也可以用 `evinedeng/jd:github`, 速度慢一点罢了

```
docker run -dit \
-v /docker/jd/scripts:/jd/scripts \
-v /docker/jd/config:/jd/config \
-v /docker/jd/log:/jd/log \
-p 5684:5678 \
--name jd \
--hostname jd \
--restart always \
evinedeng/jd:gitee
```

## 第三步: 启动 Docker 服务

`service docker start`

## 第四步: 查看创建日志

`docker logs -f jd`

> 直到出现容器启动成功...字样才代表启动成功, 按 Ctrl+C 退出查看日志

## 第五步：验证

手动立即跑一次 `jd_fruit.js` 脚本

`docker exec -it jd bash jd.sh fruit now`

- 输出 `"请先获取Cookie"` 则视为成功

  - 如果使用 `evinedeng/jd:github` 的请耐心等待再试上面那句代码

## 第六步: 编辑文件

### 方法一：在 CentOS 中编辑

```
cd /docker/jd/config
```

`vi auth.json`
> auth.json 文件是用户账号和密码, 修改完按 ESC 输入 :wq 保存并退出

`vi congif.sh`
> config.sh 文件是脚本变量设置, 按文件内说明即可, 修改完按 ESC 输入 :wq 保存并退出

`vi crontab.list`
> crontab.list 文件是脚本运行时间, 按文件内格式编写修改完按 ESC 输入 :wq 保存并退出

### 方法二：在线编辑

首先在服务器的防火墙中添加规则

- 协议: `TCP` 端口: `5684`

浏览器访问 http://<ip>:5684

- ip 即为你服务器的外网 ip

- 初始账号密码分别为 `admin` `adminadmin`