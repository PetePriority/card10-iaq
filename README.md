# Installation
## Install docker and docker-compose
```
sudo apt-get update && sudo apt-get upgrade
curl -sSL https://get.docker.com | sh
```

## Add user to docker group
```
sudo usermod -aG docker ${USER}
```
Logout and login again.

## Set docker environment variables
Copy `env.example` to `.env` and choose a secret password.

## Pull and build docker images
```
docker-compose up -d
```

## Create influx database
Start influx-CLI to create users and databases:
```
docker-compose exec influxdb influx
```

In the influx-CLI:
```
create database card10
create user "nodered" with password 'supersecure'
create user "grafana" with password 'supersecure'
grant all on card10 to nodered
grant all on card10 to grafana
exit
```
