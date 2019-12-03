# Tips for Deploying NGINX (Official Image) with Docker

## Reference

- [Docker Official Images](https://hub.docker.com/_/nginx)
- [Setting up SSL certificates for Nginx in Docker Environment](https://medium.com/faun/setting-up-ssl-certificates-for-nginx-in-docker-environ-e7eec5ebb418)
- [SSL For Free](https://www.sslforfree.com/)

## Simple Usage

    HTTP_PROXY=http://192.168.109.131:1080/ docker pull nginx:1.17
    docker tag nginx:1.17 nginx
    docker run --name nginx -d -p 80:80 nginx
    # docker cp nginx:/etc/nginx/nginx.conf .

### Hosting some simple static content

    docker run --name nginx-static -v $(pwd)/html:/usr/share/nginx/html:ro -p 8080:80 -d nginx

### Setting Up SSL Certificates

    docker run --name nginx -v $(pwd)/html:/usr/share/nginx/html:ro -v $(pwd)/nginx-ssl.conf:/etc/nginx/conf.d/ssl.conf -v $(pwd)/certs:/etc/nginx/certs:ro -d -p 80:80 -p 443:443 nginx

## Docker Compose

[docker-compose.yml](./docker-compose.yml)