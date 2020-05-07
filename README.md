# rpi-ci
teamcity docker image run on raspberry-pi

# install docker

```
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker pi
```

# install docker-compose

```
sudo apt-get install -y libffi-dev libssl-dev
sudo apt-get install -y python3 python3-pip
sudo apt-get remove python-configparser
sudo pip3 install docker-compose
```

# run docker-compose

```
cd teamcity-ubuntu
docker-compose up -d
```

# enable buildx

https://docs.docker.com/buildx/working-with-buildx/

```
docker buildx create mybuilder
docker buildx use mybuilder
```

# build image

```
#platforms: linux/amd64, linux/arm64, linux/armv7
docker buildx build --platform linux/amd64 -t sunpaq/teamcity-ubuntu:amd64 . --load
```

# push image

```
docker push sunpaq/teamcity-ubuntu:armv7
```
