# Docker


#### Docker run
```
sudo docker run hello-world
```

#### Docker ps - verificar os containers
```
docker ps
```

#### Docker ps - verificar os containers
```
docker ps -a
```

#### Docker sleep
```
docker run ubuntu sleep 1d
```

#### Docker exec bash
```
docker exec -it <id_container> bash
```

#### Docker stop
```
docker stop <id_container> -t=0
```

#### Docker stop all container
```
docker stop $(docker container ls -aq)
```

#### Docker remover
```
docker rm <id_container>
docker rm $(docker container ls -aq)
docker rmi $(docker container ls -aq)

```

#### Docker start
```
docker start <id_container>
```

#### Docker Port list
```
docker port <id_container>
```

#### Docker criar image com port forward default
```
docker run -d -P <image/container>
```

#### Docker criar image com port forward specific port
```
docker run -d -p 8080:80 <image/container>
```

#### Docker inpect - informações da imagem
```
docker inspect <id_container>
```

#### Docker layers - verificar as camadas da imagem
```
docker history <id_container>
```

#### Docker criar propria image
```
docker build -t minhaimage/app-node:1.0 .
```

#### Docker login
```
docker login -u <userdocker>
```

#### Docker push
```
docker push <userdocker/image:version>
```

#### Docker renomear
```
docker tag <oldname/image:version> <userdocker/image:version>
```

#### Docker persistir armazenagem
```
docker run -it -v /home/user/volume-docker:/app <userdocker/image:version>
docker run -it --mount type=bind,source=/home/user/volume-docker,target=/app <userdocker/image:version>
```

#### Docker novo volume
```
docker volume create meu-volume
docker volume ls
```

#### Docker novo rede bridge
```
docker network create --driver bridge minha-rede-bridge
docker run -d --name ubuntu1 --network minha-bridge ubuntu
```


# Docker Machine

#### create machine
`docker-machine create -d virtualbox vm1`

#### listar machine
`docker-machine ls`


#### machine start
`docker-machine start vm1`


#### machine ssh
`docker-machine ssh vm1`

#### init swarm
`docker swarm init --advertise-addr 192.168.99.112`


#### verificar o swarm no docker
`docker info`


#### adicionar workers
`docker swarm join --token <token_gerado no primeiro vm1> 192.168.99.112:2377`

#### recuperar token
`docker swarm join-token worker`

#### listar nó
`docker node ls`

#### down worker
`docker swarm leave`

#### remover nó 
`docker node rm <id_node do worker>`

#### docker create service
`docker service create -p 8080:3000 <userdocker/image>`

#### listar task
`docker service ls`


#### deploy de multi machine
`docker stack deploy --compose-file docker-compose.yml vote`