## Step 1: Create a second container

The installation location of `Docker` in the following code is `/docker/`,

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

Compare the following code for creating a container for the first time

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

Comparison table

||First|Second|
|:-:|:-:|:-:|
|Storage path|`/docker/jd/`|`/docker/jd2/`|
|Open port|`-p 5684:5678`|`-p 5685:5678`|
|Container name|`--name jd`|`--name jd2`|

## Step 2: View the creation log

```
docker logs -f jd
```

> Until the words `容器启动成功...` appears, it means the start is successful, press `Ctrl+C` to exit and view the log

## Step 3: git_pull

```
docker exec -it jd bash git_pull
```

## Step 4: Verify that the installation is successful

Run the `jd_fruit.js` script immediately once manually

```
docker exec -it jd bash jd.sh fruit now
```

- Output `"请先获取Cookie..."`, it will be regarded as successful

## Step 5: Edit the file

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

### Method 2: online editing

|Advantages|Disadvantages|
|:-:|:-:|
|more convenient|modify server's firewall|

1. Add rules in the server's firewall, Protocol: `TCP` , Port: `5685`

2. Use a browser to access `http://<ip>:5685`

- `ip` is the external network of your server `ip`

- The initial account password is `admin` and `adminadmin`

## Step 3: learn more commands

[Learn to use frequently used Docker commands](https://github.com/YamTian/Notes/blob/main/JD-Docker/Command.md)

