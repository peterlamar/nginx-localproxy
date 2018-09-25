# nginx-localproxy

Local reverse proxy demonstration of nginx.

## Build

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
