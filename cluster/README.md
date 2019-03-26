# Swarm Cluster
Swarm Cluster. registry, manger, workernodes

## start dind containers
```
docker-compose -f cluster-dind_docker-compose.yml up -d
docker-compose ps
```

## init config for cluster
```
docker exec -it manager docker swarm init
JOIN_TOKEN=$(docker exec -it manager docker swarm join-token manager)
docker exec -it worker(01|02|03) docker swarm join --token ${JOIN_TOKEN} manager:2377
docker exec -it manager docker node ls
```

## push docker image to registry
```
docker image push (localhost|registry):5000{repositry}:{tag}
```

## stop container
```
docker exec -it node-line-notify /bin/sh
```

## pull docker image from registry
```
docker exec -it worker(01|02|03) docker image pull registry:5000{repositry}:{tag}
docker exec -it worker(01|02|03) docker image ls
```

## check logs
```
docker logs node-line-notify
```




