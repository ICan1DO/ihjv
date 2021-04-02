### Step 1: Login Docker Hub

```
docker login
```

1. Input your docker hub name.

2. Input your password.

### Step 2: View images

```
docker images
```

### Step 3: Save image

```
docker save -o xxxxxx.tar.gz REPOSITORY:TAG
```

### Step 4: Import local Image

```
cat xxxxxx.tar.gz | docker import - new_repository_name:latest1
```

### Step 5: Change Tag

```
docker tag new_repository_name:latest1 docker_hub/docker_repository:latest2
```

### Step 6: Push

```
docker push docker_hub/docker_repository:latest2
```