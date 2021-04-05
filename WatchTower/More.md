## 选择性更新

### 选择性自动更新

在启动命令末尾添加 `容器名`

- `容器名` 可以使用 docker ps 查看 `NAME`

### 选择性排除更新

在启动命令中加入一行 `--label=com.centurylinklabs.watchtower.enable=false \`

在启动命令末尾添加 `容器名`

- `容器名` 可以使用 docker ps 查看 `NAME`

## 自动清除旧镜像

在启动命令末尾加添 `--cleanup`

## 设置自动更新频率

在启动命令末尾添加以下**二选一**的命令即可

- `–interval` 设置间隔更新时间 单位是秒

- `–schedule` 设置定时更新时间 使用 cron 表达式

## 手动更新

使用以下启动命令

```
docker run --rm \
-v /var/run/docker.sock:/var/run/docker.sock \
containrrr/watchtower \
--cleanup \
--run-once
```