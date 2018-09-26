# nginx-localproxy

Local reverse proxy demonstration of nginx.

## Docker Build

Build the local reverseproxy image with the nginx conf baked in

```
docker build . -t reverseproxy
```

Stand up containers

```
docker-compose up
```

Visit [localhost:8080](http://localhost:8080) and
[localhost:8081](http://localhost:8081) to observe the two containers proxied
seperately.

## Manual

Nginx can be installed locally on a mac with the following steps:

```
brew install nginx
```

Setup launchd to start nginx on login and now
```
brew services start nginx
```
Change /usr/local/etc/nginx/nginx.conf to following

```
worker_processes  1;

events {
    worker_connections 1024;
}

http {
    server {
        listen 8080;
        server_name localhost;

        location / {
            proxy_pass http://YOUR_DOMAIN:YOUR_PORT;
        }
    }
}
```
