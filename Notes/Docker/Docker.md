```
docker image ls
```
 : shows images docker

`docker run [nameImageDocker]` :
run an image docker with his name

`docker pull busybox` : download the image "busybox"

See a list of all containers:

```
docker container ls -a
```

We can even copy the file we created:

```
docker cp <ID>:message.txt ./
```