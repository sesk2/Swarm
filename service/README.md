# Swarm service
Service for Swarm

## run service
```
docker exec -it manager \
 docker service create --replicas 1 -publish {port}:{port} --name {name} registry:5000{repositry}:{tag}
docker exec -it manger docker service ls
```

## scale service
```
docker exec -it manager docker service scale {service name}={number of the service}
dokcer exec -it manager docker service ps
```

## remove service
```
docker exec -it manager docker service rm {service name}
```





