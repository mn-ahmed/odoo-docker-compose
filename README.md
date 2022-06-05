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
Sample docker-compose file
```
version: '1.0'
services:
  web:
    image: odoo:15.0
    container_name: odoo_15
    depends_on:
      - db
	ports:
	  - "90015:8069"
	  - "80015:8072" # For live chat
	volumes:
      - ./odoo:/var/lib/odoo
      - ./etc:/etc/odoo
      - ./addons:/mnt/extra
      - ./enterprise:/mnt/enterprise
    environment:
      - HOST=db
      - USER=odoo15
      - PASSWORD=odoo15@strong_password
  db:
    image: postgres:12
    container_name: postgres_12
    ports:  
      -5432:5432
    volumes:  
      - ./postgres:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=odoo15@strong_password
      - POSTGRES_USER=odoo15
      - POSTGRES_DB=postgres 
```
And a sample odoo.conf add inside ./etc/odoo.conf
```
nano etc/odoo.conf
```
```
admin_passwd = admin_password
db_host = db
db_user = odoo15
db_password = odoo15@strong_password
db_port = 5432
addons_path = /mnt/extra-addons
proxy_mode = True
data_dir = /var/lib/odoo
```
Then run:
```
sudo docker-compose up -d
```
Now open Odoo from localhost:90015 or server_ip:90015






