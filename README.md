# nginx-localproxy

Local reverse proxy demonstration of nginx.

## Docker Build

Stand up containers

```
docker-compose up
```

Visit [localhost](http://localhost) and observe container with proxy in effect

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
