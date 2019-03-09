# nginx-localproxy

Local reverse proxy demonstrations of nginx. This is a useful pattern to avoid cross-site scripting errors between front-end api calls to a backend server. It can also be used to simulate production deployments of legacy applications. 

## Example1, simple local docker redirect

Change into example1 dir

```
cd example1
```

Stand up containers

```
docker-compose up
```

Visit [localhost](http://localhost) and observe container with proxy in effect

## Example2

Build example dockerfile

```
docker build . -t handler
```

Stand up containers

```
docker-compose up
```

Test 1

Internet browser to [localhost](http://localhost) and observe base traffic is handled.

Test 2

Internet browser to [localhost/path/](http://localhost/path/)


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
