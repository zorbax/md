### List images in docker
```
docker images
docker search debian
docker pull debian:stretch
```
### List images
```
docker images

docker run -it IMAGE_ID /bin/bash
```
### List process
```
docker ps -a
```
### List only ID of containers
```
docker ps -q
```
### Start CONTAINER
```
docker start CONTAINER_ID
docker attach CONTAINER_ID
```
### Stop CONTAINER

```
docker stop 034bc166f0d1
```
### Stop and remove containers
```
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)

docker ps -q | xargs -r docker stop
```
### List images id
```
docker images -a
```
### Remove images
```
docker rmi IMAGE_ID1 IMAGE_ID2
```
### Get latest container ID
```
alias dl="docker ps -l -q"
```
### Get container process
```
alias dps="docker ps"
```
### Get process included stop container
```
alias dpa="docker ps -a"
```
### Get images
```
alias di="docker images"
```
### Get container IP
```
alias dip="docker inspect --format '{{ .NetworkSettings.IPAddress }}'"
```
### Stop all containers
```
dstop() { docker stop $(docker ps -a -q); }
```
### Remove all containers
```
drm() { docker rm $(docker ps -a -q); }
```
### Stop and Remove all containers
```
alias drmf='docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)'
```
### Remove all images
```
dri() { docker rmi $(docker images -q); }
```
### Dockerfile build, e.g., $dbu tcnksm/test
```
dbu() { docker build -t=$1 .; }
```
### Show all alias related docker
```
dalias() { alias | grep 'docker' | sed "s/^\([^=]*\)=\(.*\)/\1 => \2/"| sed "s/['|\']//g" | sort; }
```
### Bash into running container
```
dbash() { docker exec -it $(docker ps -aqf "name=$1") bash; }
```
### remove exited containers:
```
docker ps --filter status=dead --filter status=exited -aq | xargs -r docker rm -v
```
### remove unused images:
```
docker images --no-trunc | grep '<none>' | awk '{ print $3 }' | xargs -r docker rmi
```
### remove unused volumes:
```
find '/var/lib/docker/volumes/' -mindepth 1 -maxdepth 1 -type d | grep -vFf <(
  docker ps -aq | xargs docker inspect | jq -r '.[] | .Mounts | .[] | .Name | select(.)'
) | xargs -r rm -fr
```
### Stopping Docker containers by image name

```
while
do
  docker rm $(docker stop $(docker ps -a -q --filter ancestor=<image-name> --format="{{.ID}}")) 2>/dev/null
done

docker rm $(docker stop $(docker ps -a -q --filter ancestor=<image-name> --format="{{.ID}}"))
```
### Remove <none> images after building
```
docker rmi -f $(docker images -f "dangling=true" -q --no-trunc) 2>/dev/null
```

# Push docker to Dockerhub
```
docker login --username=atgenomics --email=atgenomics[at].com
docker tag qiime2 atgenomics/qiime2
docker push atgenomics/qiime2
```
