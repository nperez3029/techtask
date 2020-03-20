## How to build 
1) Set your secret in `.env`
> SECRET=EGZk0r5buXc5YlKHpoMaluUxNkzIq

2) Set your secret in `docker-compose.yaml`

Note:
make sure "--build-arg SECRET=" matches the content of .env


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
> https://localhost/EGZk0r5buXc5YlKHpoMaluUxNkzIq/index.html




## What's included? 
after deploying the solution, two containers will be created. 

```
$ docker ps
CONTAINER ID        IMAGE                                          COMMAND                  CREATED             STATUS                 PORTS                                                                                                                                                                                        NAMES
fa70308c321b        web:latest                                     "nginx -g 'daemon of…"   2 minutes ago       Up 2 minutes           80/tcp                                                                                                                                                                                       web
43b8570f3cd1        proxy:latest                                   "nginx -g 'daemon of…"   2 minutes ago       Up 2 minutes           0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp
```


Secrets are saved on the `web` container. 

The `proxy` container will handle authentication. 






