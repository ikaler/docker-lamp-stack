# Docker LAMP Stack Setup

## Setup LAMP environment using Docker with SSL

Custom docker images for PHP/MySQL Applications

- apache
- php (7.4)
- mysql (5.7)

This update has SSL support. You will need to create SSL certificate for this and
place them under `apache\ssl` folder.

### Build custom images

```
$ docker image build --no-cache -f php74.Dockerfile -t php74-apache-ssl-dev .
$ docker image build --no-cache -f mysql57.Dockerfile -t mysql57-dev .
```

### Start all containers:

```
$ docker-compose up -d
```

### Stop all containers

```
$ docker-compose down
```

### Access containers via terminal:

```
$ docker exec -it ${CONTAINER_PREFIX}-apache-webserver /bin/bash
$ docker exec -it ${CONTAINER_PREFIX}-mysql /bin/bash
```

### To browse website

Add following entry in `/etc/hosts` file

```
127.0.0.1       website.local
```

Access via HTTP using `http://website.local:8080`
Access via HTTPS using `https://website.local:8443`

### VSCODE Xdebug Config settings

```
{
    "name": "Listen for XDebug on Docker",
    "type": "php",
    "request": "launch",
    "port": 9000,
    "log": true,
    "externalConsole": false,
    "stopOnEntry": false,
    "pathMappings": {
        "/var/www": "${workspaceFolder}/src"
    },
}
```
