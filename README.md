# Introduction

This docker configuration will create 3 containers to kickstart your LAMP development

* db - mysql version 5.7
* php - php 5.6 + apache
* phpmyadmin

## Installation

* Install [docker](https://docs.docker.com/engine/installation/)
* Install [vagrant](https://www.vagrantup.com/downloads.html) (if using mac or windows)

```
# once everything is installed, clone this repo
git clone https://github.com/bernardpeh/docker-lamp
cd docker-lamp

# Optional step - if using mac or windows
vagrant up

cd myproject
docker-compose up -d
```

## Customisation

* edit docker-compose.yml and Dockerfile in individual folders. They should be easily understood.
* To preload a mysql script, overwrite mysql/db.sql


## Tips

* for mac and windows users, you will find that its much faster to use nfs or samba for file sharing, and hence the reason why we need another vagrant vm.

## Acknowledgement

* vagrant script from https://github.com/blinkreaction/boot2docker-vagrant
