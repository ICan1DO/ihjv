## Step 1: View images

```
docker images
```

## Step 2: Save image

```
docker save -o xxxxxx.tar.gz REPOSITORY:TAG
```

## Step 3: Import local Image

```
cat xxxxxx.tar.gz | docker import - new_repository_name:latest1
```

### Step 4: Change Tag

```
docker new_repository_name:latest1 docker_hub/docker_repository:latest2
```

### Step 5: Push

```
docker push docker_hub/docker_repository:latest2
```