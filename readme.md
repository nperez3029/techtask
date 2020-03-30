## How to build 
1) Set your secret in `.env`
> SECRET=EGZk0r5buXc5YlKHpoMaluUxNkzIq1

2) Set your secret in `docker-compose.yaml`

Note:
make sure "SECRET" matches the content of .env


```
    build:
      context: ./proxy
      args:
        - SECRET=EGZk0r5buXc5YlKHpoMaluUxNkzIq1
```

```
    build:
      context: ./web
      args:
        - SECRET=EGZk0r5buXc5YlKHpoMaluUxNkzIq1
```

3) deploy the solution 
> docker-compose up -d --build






## How to use the solution 
1) Credentials defined:
> user:password

2) Using a private browser, connect to the following URL:  
> https://x.x.x.x/EGZk0r5buXc5YlKHpoMaluUxNkzIq/index.html




## What's included? 
after deploying the solution, two containers will be created. 

```
$ docker ps
CONTAINER ID        IMAGE                                          COMMAND                  CREATED             STATUS                 PORTS                                                                                                                                                                                        NAMES
fa70308c321b        web:latest                                     "nginx -g 'daemon of…"   2 minutes ago       Up 2 minutes           80/tcp                                                                                                                                                                                       web
43b8570f3cd1        proxy:latest                                   "nginx -g 'daemon of…"   2 minutes ago       Up 2 minutes           0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp
```


Secrets are saved on the `web` container. The 'web' container will listen on the docker network 'pan' using tcp 80. 

The `proxy` container listens on tcp 80 and 443 for all interfaces. This container will handle authentication, redirect http traffic to https and only serve traffic if the client presents the correct URI to the reverse proxy. 



