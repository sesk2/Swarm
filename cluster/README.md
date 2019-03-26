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
docker exec -it manager docker swarm join-token -q worker
 output: {JOINT_TOKEN}
docker exec -it worker01 docker swarm join --token ${JOIN_TOKEN} manager:2377
docker exec -it worker02 docker swarm join --token ${JOIN_TOKEN} manager:2377
docker exec -it worker03 docker swarm join --token ${JOIN_TOKEN} manager:2377
docker exec -it manager docker node ls
```

## push docker image to registry
```
docker image push (localhost|registry):5000{repositry}:{tag}
```

## stop cluster
```
docker 
```

## pull docker image from registry
```
docker exec -it {node name} docker image pull registry:5000{repositry}:{tag}
docker exec -it {node name} docker image ls
```

## add node to cluster
```
# worker
docker exec -it mangaer docker swarm join-token -q worker
docker exec -it {node name} docker swarm join --token {JOIN_TOKEN} manager:2377
# manger
docker exec -it mangaer docker swarm join-token -q manager
docker exec -it {node name} docker swarm join --token {JOIN_TOKEN} manager:2377
```

## remove node from cluster
```
# worker
docker exec -it {node name} docker swarm leave -f
docker exec -it manager docker rm {node name}
docker exec -it manager docker node ls
#manger
docker exec -it {node name} docker swarm leave -f
docker exec -it {other manger} docker node demote {node name}
docker exec -it manager docker rm {node name}
docker exec -it {other manger} docker node ls
```

## check logs
```
docker logs {node name}
```




