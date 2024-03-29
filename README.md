# Docker

### Docker run

```bash
sudo docker run hello-world
```

### Docker ps - verificar os containers

```bash
docker ps
```

### Docker ps - verificar os containers

```bash
docker ps -a
```

### Docker sleep

```bash
docker run ubuntu sleep 1d
```

#### Docker exec bash

```bash
docker exec -it <id_container> bash
```

#### Docker stop

```bash
docker stop <id_container> -t=0
```

#### Docker stop all container

```bash
docker stop $(docker container ls -aq)
```

#### Docker remover

```bash
docker rm <id_container>
docker rm $(docker container ls -aq)
docker rmi $(docker container ls -aq)

```

#### Docker start

```bash
docker start <id_container>
```

#### Docker Port list

```bash
docker port <id_container>
```

#### Docker criar image com port forward default

```bash
docker run -d -P <image/container>
```

#### Docker criar image com port forward specific port

```bash
docker run -d -p 8080:80 <image/container>
```

#### Docker inpect - informações da imagem

```bash
docker inspect <id_container>
```

#### Docker layers - verificar as camadas da imagem

```bash
docker history <id_container>
```

#### Docker criar propria image

```bash
docker build -t minhaimage/app-node:1.0 .
```

#### Docker login

```bash
docker login -u <userdocker>
```

#### Docker push

```bash
docker push <userdocker/image:version>
```

#### Docker renomear

```bash
docker tag <oldname/image:version> <userdocker/image:version>
```

#### Docker persistir armazenagem

```bash
docker run -it -v /home/user/volume-docker:/app <userdocker/image:version>
docker run -it --mount type=bind,source=/home/user/volume-docker,target=/app <userdocker/image:version>
```

#### Docker novo volume

```bash
docker volume create meu-volume
docker volume ls
```

#### Docker novo rede bridge

```bash
docker network create --driver bridge minha-rede-bridge
docker run -d --name ubuntu1 --network minha-bridge ubuntu
```

# Docker Machine

#### create machine

```bash
docker-machine create -d virtualbox vm1
```

#### listar machine

```bash
docker-machine ls
```

#### machine start

```bash
docker-machine start vm1
```

#### machine ssh

```bash
docker-machine ssh vm1
```

#### init swarm

```bash
docker swarm init --advertise-addr 192.168.99.112
```

#### verificar o swarm no docker

```bash
docker info
```

#### adicionar workers

```bash
docker swarm join --token <token_gerado no primeiro vm1> 192.168.99.112:2377
```

#### recuperar token

```bash
docker swarm join-token worker
```

#### listar nó

```bash
docker node ls
```

#### down worker

```bash
docker swarm leave
```

#### remover nó

```bash
docker node rm <id_node do worker>
```

#### docker create service

```bash
docker service create -p 8080:3000 <userdocker/image>
```

#### listar task

```bash
docker service ls
```

#### deploy de multi machine

```bash
docker stack deploy --compose-file docker-compose.yml vote
```
