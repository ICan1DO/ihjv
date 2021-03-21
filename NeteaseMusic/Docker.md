### PC

```
docker run -d -p 2020:8080 --name music_ios --restart always nondanee/unblockneteasemusic
```

### iOS

```
docker run -d -p 2021:8080 --name music_ios --restart always nondanee/unblockneteasemusic -s -e https://music.163.com
```
