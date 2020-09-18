# Docker commands hand book

## Format Docker ps output

```
$ docker ps -a --format 'CONTAINER ID : {{.ID}} | Name: {{.Names}} | Image:  {{.Image}} |  Ports: {{.Ports}}'
```

### Docker build
```
$ docker build -q --no-cache -t ${IMAGE}:${VERSION} .
```

### Docker run 
```
$ docker run -it --user=root -p 8000:8080 ${IMAGE}:${TAG} sh
or
$ docker run --name flask -e AUTHOR="Preethi" -d -P flask:1.0
```


## Docker Volumes
Docker volume common commands

```
$ docker volume create test_vol
$ docker volume ls
$ docker volume inspect test_vol
```







## Docker container, image, volume, network removal commands

### Remove all stopped containers, dangling images, and unused networks
```
$ docker system prune

# The above command does not remove volume to remove volume then

$ docker system prune --volumes
```

### Container list stop and remove commands
```
$ docker container ls -a
$ docker container ls -a --filter status=exited --filter status=created

$ docker container stop $(docker container ls -aq) 
# or 
$ docker container stop $(docker ps -a --format '{{.ID}}')

$ docker container rm cc3f2ff51cab cd20b396a061 (Container Ids)
$ docker container rm $(docker container ls -aq) 
# or 
$ docker container rm $(docker ps -a --format '{{.ID}}')

$ docker container prune
$ docker container prune --filter "until=12h" 
```

### Image list and remove commands
```
$ docker image ls

$ docker image rm 75835a67d134 2a4cca5ac898
$ docker image prune
# Below command removes all the images that are not referenced by any existing container
$ docker image prune -a
$ docker image prune -a --filter "until=12h"
$ docker rmi image_id
```

### Docker Volumes list and remove commands
```
$ docker volume ls
$ docker volume rm volume_ids
$ docker volume prune
```

### Docker Networks list and remove commands
```
$ docker network ls
$ docker network rm c520032c3d31 (network ids)
$ docker network prune
$ docker network prune -a --filter "until=12h"
```

### Docker information
```
$ docker info
```
