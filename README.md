# Introduction

This docker configuration will create a vagrant vm with 3 containers to kickstart your LAMP development.

* db - mysql version 5.7
* php - php 5.6 + apache
* phpmyadmin

vagrant script from https://github.com/blinkreaction/boot2docker-vagrant - thankyou.

Why do we need vagrant? Because for mac and windows users, its much faster to use nfs or samba for file sharing. For linux users, you dont need this workaround.

## Installation
Install the pre-requisites as documented in https://github.com/blinkreaction/boot2docker-vagrant

```
# remember to add this line to ~/.bash_profile. 
# This will allow us to run docker commands on host machine mapped to the vagrant vm.
DOCKER_HOST="tcp://192.168.10.10:2375"
source ~/.bash_profile
```

Next,

```
# clone this repo
git clone https://github.com/bernardpeh/docker-lamp
cd docker-lamp
vagrant up
cd myproject
docker-compose up -d
```

To test that everything is working correctly, go to these urls. They should work

```
http://192.168.10.10:8080 (your website on port 80)
https://192.168.10.10:8081 (your website on port 443)
http://192.168.10.10:8082 (phpmyadmin)
```

## Customisation

* edit docker-compose.yml and Dockerfile in individual folders. They should be easily understood.
* To run sql post-mysql container bootup, overwrite mysql/db.sql

## Tips

* To see the logs

```
docker logs -f container_id
```

* To go to the shell of each container

```
docker exec -it container_id bash
```

* To see all the docker compose process
```
docker-compose ps
```
