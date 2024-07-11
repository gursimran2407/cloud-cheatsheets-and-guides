# Docker Installation

https://docs.docker.com/desktop/

# Commands on Hands On

```
docker --version
docker run hello-world
docker pull busybox
docker images
docker run busybox
docker run busybox echo "hello from busybox mlops"
docker ps
docker ps -a
docker run -it busybox sh
docker rm <container_id>
```

# 2. Hands On


```
docker run -d -P --name catgif gursimran2407/catgif
docker ps
docker port catgif
docker stop catgif
docker run -p 8888:5000 gursimran2407/catgif
docker build -t catgifv2 .
docker run -p 8888:5000 catgifv2
docker login
docker build -t gursimran2407/catgif-devops .
docker push gursimran2407/catgif-devops
```

