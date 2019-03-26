# Swarm Stack
Stack for Swarm

## run stack
```
docker exec -it manager docker network create --driver=overlay --attachable {network name}
docker exec -it manager docker stack deploy -c {stacks file} {stack name}
docker exec -it manager docker stack services {stack name}
docker exec -it manager docker stack ps {stack name}
```

## run visualizer
```
docker exec -it manager docker stack deploy -c {visualizer.yml} visualizer
* Access http://localhost:9000
```

## remove stack
```
docker exec -it manager docker stack rm {service name}
```





