# dockerWiki
---------------
Łączenie się do dockera:
```
docker-compose exec docker-name sh
```

Wypisanie sieci
```
docker network ls
```
Czyszczenie nieużywanych sieci ( wyłączyć wysztkie docker )
```
docker network prune
```


Wypisanie volume
```
docker volume ls
```
Czyszczenie volume
```
docker volume prune
```


Usunięcie wszystkich kontenerw Windows
```
FOR /f "tokens=*" %i IN ('docker ps -a -q') DO docker rm %i
```
Usunięcie wszystkich kontenerw Linux/Mac
```
docker rm $(docker ps -a -q)
```


Usunięcie wszystkich obrazów Windows
```
FOR /f "tokens=*" %i IN ('docker images -q -f "dangling=true"') DO docker rmi -f %i
FOR /f "tokens=*" %i IN ('docker images -a') DO docker rmi -f %i
```
Usunięcie wszystkich obrazów Linux/Mac
```
docker rmi $(docker images -q)
docker volume rm $(docker volume ls |awk '{print $2}'
```

You can see where docker is storing that volume on your hard drive by running command:
docker volume inspect docker_database



!!!!!!!!!!!!!!
Windows Docker Host - Linux container sockets (Docker Desktop Win 10)
For Docker for Windows following seems to be working:

-v //var/run/docker.sock:/var/run/docker.sock
