# Команды

#### Запуск-остановка
```
docker run -d(-it) -p 80:80 IMAGE
docker stop PID
docker stop $(docker ps -aq) 
```

#### Инспектирование
```
docker ps
docker ps -a
docker logs container_name          # вывод логов контейнеров
docker inspect container_name       # информация по запущенному контейнеру
```

#### Работа внутри контейнера
```
docker exec -it container_name bash
```

#### Авторизация в реестры
```
docker login registry.gitlab.com
```

#### Билд-пуш в реестры
```
docker build -t registry.gitlab.com/p-12s/test:ver .
docker push registry.gitlab.com/p-12s/test:ver
```

#### Работа с сетью
Виды сетей:
- bridge (по-умолчанию) - для коммуникации контейнеров в пределах одного хоста (не рекомендуется для использования в продакшене)
- overlay - распределенная сеть среди нескольких хостов Docker
- macvlan/ipvlan — контейнер подключается при помощи виртуального интерфейса, подключенного к физическому. При этом у каждого из них есть свой MAC-адрес
- host — как видно из названия, в этом случае подключение происходит к сети хоста
- none - сети нет

```
docker network ls
docker network create -d bridge NAME 
docker network connect
docker network disconnect 
docker network rm
docker network prune                    # удалит сети без подключенных контейнеров
```