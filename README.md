Sensu Complete
================

This git repo provides everything needed to deploy the latest version of [Sensu Core](https://sensuapp.org/). This includes:
* Redis
* Sensu server
* Sensu API
* Sensu client
* Uchiwa

The original Docker images were built by [sstarcher](https://github.com/sstarcher) in these projects:

- [https://github.com/sstarcher/docker-sensu]
- [https://github.com/sstarcher/docker-uchiwa]

## Install Repos

- https://github.com/sensu/sensu/tags
- https://sensu.global.ssl.fastly.net/apt/pool/bionic/main/u/uchiwa/


## Configuration

### Sensu

Custom checks and plugins are added from sensu/checks and sensu/plugins respectively.

Environment variables:

```
REDIS_HOST
REDIS_PORT
```

### Uchiwa

Default configuration allows for local linkage to sensu-api by using docker links.  If you need to reference external servers set the following variables as needed.

* Additional configuration files can be placed in ```/etc/sensu/dashboard.d```

```    
UCHIWA_BIND 0.0.0.0
UCHIWA_SERVICE_PORT 3000
UCHIWA_REFRESH 10
UCHIWA_LOG_LEVEL info

Optional:
SENSU_DC_NAME
SENSU_HOSTNAME
SENSU_SERVICE_PORT 4567
```

* Check data is pulled from the Sensu API.  Checks will only show up in Uchiwa if they are locally on the machine running the Sensu API.

## Deploying with Docker

```
docker-compose up -d
```

## Deploying with Kubernetes

```
kubectl create namespace sensu-system
```
