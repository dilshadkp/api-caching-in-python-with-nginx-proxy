# Dockerization of API caching python application with nginx loadbalancing

## Description
This is a documentation explaing dockerization of an api caching project in python. This project is designed with an nginx proxy loadbalancer to loadbalance the traffic among api containers and a Redis cache container for api caching. 
All the communications between the containers are through a bridge network inside the host server.

I used [ipstack](https://ipstack.com/) API in this python application as a demo. This API will show you the Geolocation of IP addresses.

## Architecture
![](https://i.ibb.co/0DWG0Cc/ipstack.png)

----
## Features
- IP-Location finding website (Python) (Just a demonstration)
- Easy to migrate everywhere 
- Container load balanced (Nginx)
- All containers are spin up with a single command

---
## Includes
- 5 Containers for LAMP (IP-Stack, Redis, Nginx(Load Balancer))
- 1 Network (For Container interconnecting)

----
## Prerequisites
- Need to install docker and docker-compose
- You have a basic knowledge of what is docker.
- You have a basic knowledge of what is ipstack and how it's working
- Need an IP stack Login and API for location finding
- Need to add apikey file before running the script. So, please find the IP stack URL and grab the key and change the same on "env.dev" 

-----
## How to install docker and docker-compose.
### Docker installation 
Please refer the doc for [docker installation](https://docs.docker.com/engine/install)

```sh
yum install docker -y
yum install git -y
```
### docker-compose installation
Please refer the doc for [docker-compose installation](https://docs.docker.com/compose/install/)
```sh
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
sudo chmod +x /usr/bin/docker-compose
docker-compose version 
```
> you guys can use [play with Docker](https://labs.play-with-docker.com/) which includes pre-installed docker and compose. It looks like a terminal and it's built from alpine OS. So, it's just used for learning purpose so who you guys can use 4hrs session without any additional installation.

## How to get IPstack API
> Please go through the [ipstack](https://ipstack.com/) and click "_GET FREE API KEY_" on the top right corner. 
![alt text](https://i.ibb.co/sFb3zz6/ipstack.png)


## How to use

- Clone application from GitHub

```sh
git clone https://github.com/dilshadkp/api-caching-with-nginx-proxy.git
cd api-caching-with-nginx-proxy
```
- Add your API KEY in _env.txt_

```sh
vim env.txt
```

```sh
IPSTACK_KEY="enter-your-key-here(without any double quotes)"
```
- Execute the _docker-compose.yml_

```sh
docker-compose --env-file env.txt up -d
```

## Output

```sh
$ docker-compose --env-file env.txt up -d
Pulling nginx (nginx:alpine)...
alpine: Pulling from library/nginx
97518928ae5f: Pull complete
a4e156412037: Pull complete
e0bae2ade5ec: Pull complete
3f3577460f48: Pull complete
e362c27513c3: Pull complete
a2402c2da473: Pull complete
Digest: sha256:12aa12ec4a8ca049537dd486044b966b0ba6cd8890c4c900ccb5e7e630e03df0
Status: Downloaded newer image for nginx:alpine
Pulling redis (redis:latest)...
latest: Pulling from library/redis
eff15d958d66: Pull complete
1aca8391092b: Pull complete
06e460b3ba1b: Pull complete
def49df025c0: Pull complete
646c72a19e83: Pull complete
db2c789841df: Pull complete
Digest: sha256:619af14d3a95c30759a1978da1b2ce375504f1af70ff9eea2a8e35febc45d747
Status: Downloaded newer image for redis:latest
Pulling ipstack1 (dilshadkp/ipstack:v1)...
v1: Pulling from dilshadkp/ipstack
921b31ab772b: Pull complete
1a0c422ed526: Pull complete
ec0818a7bbe4: Pull complete
b53197ee35ff: Pull complete
8b25717b4dbf: Pull complete
2352f0e22307: Pull complete
0148c4900674: Pull complete
f2b28ffe4f9b: Pull complete
c5b6db6af2f3: Pull complete
Digest: sha256:db19eb2d4030d4fb34bcc9e385d9153646a6ed8d468fe4b60fcbe20a64fe65cd
Status: Downloaded newer image for dilshadkp/ipstack:v1
Creating ipstack3 ... done
Creating redis    ... done
Creating ipstack1 ... done
Creating ipstack2 ... done
Creating nginx    ... done
```

##### Containers list

```sh
$ docker ps
CONTAINER ID   IMAGE                  COMMAND                  CREATED         STATUS         PORTS                NAMES
3000ec757706   nginx:alpine           "/docker-entrypoint.…"   6 minutes ago   Up 5 minutes   0.0.0.0:80->80/tcp   nginx
2572923cba63   dilshadkp/ipstack:v1   "python3 app.py"         6 minutes ago   Up 5 minutes                        ipstack2
1bd7fa355204   dilshadkp/ipstack:v1   "python3 app.py"         6 minutes ago   Up 6 minutes                        ipstack3
f59f3a48d583   redis:latest           "docker-entrypoint.s…"   6 minutes ago   Up 5 minutes   6379/tcp             redis
cf995a8acbc1   dilshadkp/ipstack:v1   "python3 app.py"         6 minutes ago   Up 6 minutes                        ipstack1ck1
```
## Sample Screenshot

![](https://i.ibb.co/FwZp3pm/site.png)

x------------------x---------------------x---------------------x-------------------x--------------------x---------------------x-------------------x

### ⚙️ Connect with Me 

<p align="center">
<a href="mailto:dilshad.lalu@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/dilshadkp/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a> 
<a href="https://www.instagram.com/dilshad_a.k.a_lalu/"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white"/></a>
<a href="https://wa.me/%2B919567344212?text=This%20message%20from%20GitHub."><img src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white"/></a><br />

