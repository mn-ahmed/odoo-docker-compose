# Install odoo + Postgresql on ubuntu 20.04 with docker-compose
## Requireements
> Ubuntu 20.04 server, a user with sudo access

> Install [Docker](https://docs.docker.com/get-docker/)

## Manual install docker-compose

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
Set executable and permission for docker-compose
```
sudo chmod +x /usr/local/bin/docker-compose
```
Check docker-compose version
```
docker-compose --version
```
## Create directory for the project
```
mkdir -p odoo15
```
```
cd odoo15
```
## Create config, addons, odoo and postgres folders for the project environment

```
sudo mkdir -p ./etc && sudo chmod -R 777 etc
sudo mkdir -p ./addons && sudo chmod -R 777 addons
sudo mkdir -p ./enterprise && sudo chmod -R 777 entreprise #for adding the enterprise addons
sudo mkdir -p ./odoo && sudo chmod -R 777 odoo
sudo mkdir -p ./postgres && sudo chmod -R 777 postgres
```
## Create the docker-compose file
```
sudo nano docker-compose.yml
```






