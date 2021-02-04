## 第一步: 创建第二个容器

以下代码中 `Docker` 安装位置为 `/docker/`, 

```
docker run -dit \
-v /docker/jd2/scripts:/jd/scripts \
-v /docker/jd2/config:/jd/config \
-v /docker/jd2/log:/jd/log \
-p 5685:5678 \
--name jd2 \
--hostname jd2 \
--restart always \
evinedeng/jd:gitee
```

对比下面这段第一次创建容器的代码, 有些许不同, 主要有

- 第二次容器名为 `jd2`

  - `--name jd2`

- 第二次容器端口为 `5685`

  - `-p 5685:5678`

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

## 第二步: 启动 Docker 服务

~~`service docker start`~~

- 其实此步骤应该省略

## 第三步: 查看创建日志

`docker logs -f jd2`

> 直到出现 `容器启动成功...` 字样才代表启动成功, 按 `Ctrl+C` 退出查看日志

## 第四步: 验证

手动立即跑一次 `jd_fruit.js` 脚本

`docker exec -it jd bash jd.sh fruit now`

- 输出 `"请先获取Cookie"` 则视为成功

  - 如果使用 `evinedeng/jd:github` 的请耐心等待再试上面那句代码

## 第五步: 编辑文件

### 方法一: 在 CentOS 中编辑

```
cd /docker/jd/config
```

`vi auth.json`

-  `auth.json` 文件是用户账号和密码, 修改完按 `ESC` 输入 `:wq` 保存并退出

`vi congif.sh`

- `config.sh` 文件是脚本变量设置, 按文件内说明即可, 修改完按 `ESC` 输入 `:wq` 保存并退出

`vi crontab.list`

- `crontab.list` 文件是脚本运行时间, 按文件内格式编写修改完按 `ESC` 输入 `:wq` 保存并退出

### 方法二: 在线编辑

- 优点: 后期编辑文件、获取 `Cookie` 比较方便

- 缺点: 前期一般需要对服务器进行一些设置

1. 首先在服务器的防火墙中添加规则

- 协议: `TCP` 端口: `5685`

2. 浏览器访问 `http://<ip>:5685`

- `ip` 即为你服务器的外网 `ip`

- 初始账号密码分别为 `admin` 和 `adminadmin`

## 第六步: 学习更多命令

[学习使用频率较高的 Docker 命令](https://github.com/chiupam/Notes/blob/main/Docker/Command.md)