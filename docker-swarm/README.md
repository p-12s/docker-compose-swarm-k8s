# Docker swarm
Предполагается, что docker у вас уже установлен.  
Проинициализируем swarm:
```
docker swarm init
```
После создания выведется команда для будущего добавления воркеров в этот swarm:
```
docker swarm join --token SWMTKN-1-46m7bxst8502iny1j9fea66x3f04ikct4g8abc1rcmpl08s8hl-6dqafaeh0iixxap25nt7wnzhe 192.168.65.3:2377
```
либо: 
```
docker swarm join-token manager
```
и следовать инструкциям.  
Для выхода ноды из swarm:
```
docker swarm leave
```
Теперь можно увидеть запущенную ноду swarm:
```
docker node ls
```



## Сервисы
Это абстракция над 
Список запущенных:
```
docker service ls
```
Выключить сервис:
```
docker service rm PID
```

