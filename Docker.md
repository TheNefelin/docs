# Docker

[Download Doker](https://docs.docker.com/) <br>
[Download Doker Images](https://hub.docker.com/)

## Some Commands
```
docker ps
docker ps -a
docker container start <CONTAINER ID>
docker container start <CONTAINER ID> -d
docker container stop <CONTAINER ID>
docker container rm <CONTAINER ID>
docker logs <CONTAINER ID>
```

## Hub public Images
* Download image
* Create container
* Start container
* -e (environment)
* -p (ServerPort:DockerPort) (8080:80)
```
docker pull <IMAGE>
docker container create -e <ENVIRONMENT> <IMAGE>
docker container start <CONTAINER ID>
```

### SQL Server
* [download image](https://hub.docker.com/r/microsoft/mssql-server)
```
docker pull mcr.microsoft.com/mssql/server 

docker container create -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=mysecretpassword" -e "MSSQL_PID=Developer" -p 1433:1433 --name SQLServer mcr.microsoft.com/mssql/server

docker container start <CONTAINER ID>
```
* New SQL User
```
CREATE LOGIN testing WITH PASSWORD = 'testing';
GO
CREATE DATABASE db_testing
GO
USE db_testing
GO
CREATE USER testing FOR LOGIN testing;
GO
EXECUTE sp_addrolemember 'db_owner', 'testing';
GO
```

### MySQL
* [download image](https://hub.docker.com/_/mysql)
```
docker pull mysql

docker run --name MySQL -e MYSQL_ROOT_PASSWORD=mysecretpassword -p 3306:3306 -d mysql
```
* New SQL User
```
CREATE DATABASE db_testing;
USE db_testing;

CREATE USER 'testing'@'%' IDENTIFIED BY 'db_testing';
GRANT CREATE, ALTER, DROP ON db_testing.* TO 'testing'@'%';
GRANT SELECT, INSERT, UPDATE, DELETE ON db_testing.* TO 'testing'@'%';
GRANT REFERENCES ON db_testing.* TO 'testing'@'%';
```

### PostgreSQL
[download image](https://hub.docker.com/_/postgres)
```
docker pull postgres

docker run --name PostgreSQL -e POSTGRES_PASSWORD=mysecretpassword -p 5432:5432 -d postgres
```
* New SQL User
```
CREATE DATABASE db_testing;
CREATE USER testing WITH PASSWORD 'testing';
GRANT ALL PRIVILEGES ON DATABASE db_testing TO testing;
```

## Docker File

<hr>
<hr>
<hr>
<hr>

## Docker init
```
docker init
```

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
