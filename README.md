# rpi-ci
teamcity docker image run on raspberry-pi

# enable buildx

https://docs.docker.com/buildx/working-with-buildx/

```
docker buildx create

```

# build image

```
docker buildx build --platform linux/amd64, linux/arm64, linux/armv7 . --load
```

# push image

```
docker push sunpaq/teamcity-ubuntu:armv7
```

# run compose

```
cd teamcity-ubuntu
docker-compose up -d
```
