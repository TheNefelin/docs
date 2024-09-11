# Docker

[Download Doker](https://docs.docker.com/)

## Dockerfile
* Create Dockerfile
* build (Build image) 
* -t (Image name)
* . (Dockerfile route)
```
docker build -t welcome-to-docker .
```

## Multiple services in single container
* Create compose.yaml
```
services:
  todo-app:
    ...

  todo-database:
    ...
```
* Run command to build image from compose
```
docker compose up -d
```
* For host reload on deploy in docker for developing
```
docker compose watch
```
* Persist db on file siste
* add volumes to compose file
```
services:
  todo-database:
    volumes: 
      - database:/data/db

volumes:
  database:
```
