# api-caching-in-python-with-nginx-proxy
This is a sample python application with Redis caching and nginx proxy

```
[root@ip-172-31-32-196 nginx]# docker ps
CONTAINER ID   IMAGE                    COMMAND                  CREATED         STATUS         PORTS                                           NAMES
f275a3548c90   fujikomalan/ipstack:v1   "python3 app.py"         5 minutes ago   Up 5 minutes                                                   ipstack3
73c50e464287   redis:latest             "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes   6379/tcp                                        redis
d2534ec2974d   fujikomalan/ipstack:v1   "python3 app.py"         5 minutes ago   Up 5 minutes                                                   ipstack2
ebeef02f3da6   nginx:alpine             "/docker-entrypoint.…"   5 minutes ago   Up 5 minutes   80/tcp, 0.0.0.0:443->443/tcp, :::443->443/tcp   nginx
537c9c2a21c8   fujikomalan/ipstack:v1   "python3 app.py"         5 minutes ago   Up 5 minutes                                                   ipstack1
```
