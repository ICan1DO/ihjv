```
vi ~/.watchtower.list
```

```
docker run -d \
--name wat \
-v /var/run/docker.sock:/var/run/docker.sock \
containrrr/watchtower -c \
$(cat ~/.watchtower.list) \
-i 3600
```