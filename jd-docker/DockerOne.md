## Step 1: Install Docker

1. If you have installed Docker before, you need to uninstall it first

`sudo yum remove docker docker-common docker-selinux docker-engine`

2. Install

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo
sudo sed -i 's+download.docker.com+mirrors.bfsu.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo
sudo yum makecache fast
sudo yum install docker-ce
```

## Step 2: Start Docker service

```
service docker start
```

## Step 3: Create a image

Copy and paste the following code and press Enter, where the installation location of `Docker` is `/docker/`

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

## Step 4: View the creation log

```
docker logs -f jd
```

> Until the words `容器启动成功...` appears, it means the start is successful, press `Ctrl+C` to exit and view the log

## Step 5: git_pull

```
docker exec -it jd bash git_pull
```

## Step 6: Verify that the installation is successful

Run the `jd_fruit.js` script immediately once manually

```
docker exec -it jd bash jd.sh fruit now
```

- Output `"请先获取Cookie..."`, it will be regarded as successful

## Step 7: Edit the file

### Method 1: Edit in CentOS

```
cd /docker/jd/config
vi auth.json
```

-  `auth.json` User account and password. After modifying, press `ESC` and enter `:wq` to save and exit.

```
vi congif.sh
```

- `config.sh` Setting script variables.  After modifying, press `ESC` and enter `:wq` to save and exit.

```
vi crontab.list
```

- `crontab.list` Setting the running time of the javascript.  After modifying, press `ESC` and enter `:wq` to save and exit.

### Method 2: Edit Online

|Advantages|Disadvantages|
|:-:|:-:|
|more convenient|modify server's firewall|

1. Add rules in the server's firewall, Protocol: `TCP`, Port: `5684`

2. Use a browser to access `http://<ip>:5684`

- `ip` is the external network of your server `ip`

- The initial account password is `admin` and `adminadmin`

## Step 8: Learn more commands

[Learn to use frequently used Docker commands](https://github.com/chiupam/Notes/blob/main/jd-docker/Command.md)

