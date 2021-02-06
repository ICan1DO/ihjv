## Basic command query

The container in this note is named jd or jd2

### View all container conditions

`docker ps -a`

- The name of the container is under `NAMES` in the table output by the server

### Start Docker service

`service docker start`

### View creation log

`docker logs -f NAMES`

### Start, stop, kill, delete container

```
docker start NAMES
docker stop NAMES
docker kill NAMES
docker rm -f NAMES
```

### Reset control panel username and password

`docker exec -it NAMES bash jd resetpwd`

### Manually pull javascript

`docker exec -it NAMES bash git_pull`

### Manually execute the javascript

- Execute the javascript after delaying RandomDelay seconds, RandomDelay is set in config.sh

`docker exec -it NAMES bash jd.sh javascript`

- Execute javascript immediately

`docker exec -it NAMES bash jd.sh javascript now`

### Enter the container to view the hangup log

`docker exec -it NAMES /bin/bash`

Then

`pm2 monit`

Exit

`exit`

