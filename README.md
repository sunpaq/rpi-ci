# rpi-ci

multi-arch teamcity docker image:
- Mac (amd64)
- PC/Linux (amd64)
- Raspberry-Pi 1/2 (arm/v7)
- Raspberry-Pi 3/4 (arm64/v8)

# docker hub

https://hub.docker.com/r/sunpaq/teamcity-ubuntu/tags

# How to use:

## 1.install docker

```
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker pi
```

## 2.install docker-compose

```
sudo apt-get install -y libffi-dev libssl-dev
sudo apt-get install -y python3 python3-pip
sudo apt-get remove python-configparser
sudo pip3 install docker-compose
```

## 3.run docker-compose

run the following command in the folder contains **docker-compose.yml** file

```
#start server
docker-compose up -d
```

```
#stop server
docker-compose down
```

# How to customize:

## 1.download and unzip the TeamCity tar

put the tarball into **teamcity-ubuntu/dist** folder. then run the following command
```
tar zxfv TeamCity-*.tar.gz
```

please comment out the plugins you need before run this
```
./teamcity-ubuntu/remove_plugins.sh
```

## 2.enable buildx

https://docs.docker.com/buildx/working-with-buildx/

```
docker buildx create mybuilder
docker buildx use mybuilder
```

## 3.build image

platforms: linux/amd64, linux/arm64/v8, linux/arm/v7

```
cd teamcity-ubuntu
docker buildx build --platform linux/amd64 -t sunpaq/teamcity-ubuntu:amd64 . --load
```

## 4.push image

```
docker push <your-dockhub-id>/teamcity-ubuntu:amd64
```
