# Docker-PHP

## Setup LAMP environment using Docker
Custom docker images for PHP/MySQL Applications
- apache
- php (7.4)
- mysql (5.7)

### Build custom images
```
$ docker image build --no-cache -f php74.Dockerfile -t php74-apache-dev .
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

### For terminal access to Containers:
```
$ docker exec -it ${CONTAINER_PREFIX}-apache-webserver /bin/bash
$ docker exec -it ${CONTAINER_PREFIX}-mysql /bin/bash
```

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