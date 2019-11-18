# Tips for Deploying NGINX (Official Image) with Docker

## Reference

- [Docker Official Images](https://hub.docker.com/_/nginx)
- [Setting up SSL certificates for Nginx in Docker Environment](https://medium.com/faun/setting-up-ssl-certificates-for-nginx-in-docker-environ-e7eec5ebb418)

## Simple Usage

    HTTP_PROXY=http://192.168.109.131:1080/ docker pull nginx:1.17
    docker tag nginx:1.17 nginx
    docker run --name nginx -d -p 80:80 nginx
    # docker cp nginx:/etc/nginx/nginx.conf .

### Hosting some simple static content

    docker run --name nginx-static -v $(pwd)/html:/usr/share/nginx/html:ro -p 8080:80 -d nginx

## Docker Compose

[docker-compose.yml](./docker-compose.yml)