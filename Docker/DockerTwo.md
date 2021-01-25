## 第一步: 创建第二个容器

以下代码中 Docker 安装位置为 /docker/, 最后一行推荐使用 `evinedeng/jd:gitee`, 也可以用 `evinedeng/jd:github`

```
docker run -dit \
-v /docker/jd2/scripts:/jd/scripts \
-v /docker/jd2/config:/jd/config \
-v /docker/jd2/log:/jd/log \
-p 5685:5678 \
--name jd2 \
--hostname jd2 \
--restart always \
evinedeng/jd:github
```

对比下面这段第一次创建容器的代码, 有些许不同, 主要有

- 第一次容器名为 jd , 第二次容器名为 jd2

  - `--name jd2`

- 第一次容器端口为 5684, 第二次容器端口为 5685

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
evinedeng/jd:github
```

## 第二步: 启动 Docker 服务

`service docker start`

- 其实此步骤应该省略

## 第三步: 查看创建日志

`docker logs -f jd2`

> 直到出现容器启动成功...字样才代表启动成功, 按 Ctrl+C 退出查看日志

## 第四步: 编辑文件

```
cd /docker/jd2/config
```

`vi auth.json`
> auth.json 文件是用户账号和密码, 修改完按 ESC 输入 :wq 保存并退出

`vi congif.sh`
> config.sh 文件是脚本变量设置, 按文件内说明即可, 修改完按 ESC 输入 :wq 保存并退出

`vi crontab.list`
> crontab.list 文件是脚本运行时间, 按文件内格式编写修改完按 ESC 输入 :wq 保存并退出

### 手动 git pull 更新脚本

`docker exec -it jd2 bash git_pull`

> 顺便也执行以下这段代码吧 `npm install got`

### 手动删除指定时间以前的旧日志

`docker exec -it jd2 bash rm_log`

### 手动导出所有互助码

`docker exec -it jd2 bash export_sharecodes`

### 手动执行一次某个脚本

以执行名为 jd_fruit.js 的文件为例 

`docker exec -it jd2 bash jd.sh jd_fruit now`

其中 `exec` 后面的 `jd2` 为容器名, `bash` 后面的 `jd` 为命令名, `xxx` 为 `lxk` 的脚本名