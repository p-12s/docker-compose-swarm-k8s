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
