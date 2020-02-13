# How To Pass Environment Info During Docker Builds

- [How To Pass Environment Info During Docker Builds](https://blog.bitsrc.io/how-to-pass-environment-info-during-docker-builds-1f7c5566dd0e)
- [busybox](https://hub.docker.com/_/busybox) `docker pull busybox:1.31`


## Sample Code

    ARG VERSION=latest
    FROM busybox:$VERSION
    ARG VERSION
    RUN echo $VERSION > image_version

    # docker build -t <image-name>:<tag> --build-arg <key1>=<value1> --build-arg <key2>=<value2> .
    docker build -t tmp:latest --build-arg VERSION=1.31 -f Dockerfile.test .
    # cat image_version
    docker run -it --rm tmp cat image_version