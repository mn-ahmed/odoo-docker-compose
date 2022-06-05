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




