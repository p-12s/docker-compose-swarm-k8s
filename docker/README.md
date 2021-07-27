# Docker

### Multistage - сборка
```
FROM golang:1.16.5-buster AS build
...
FROM alpine:latest
COPY --from=build /app /app
```
Если итоговый файл - только бинарник (например, Go):
```
...
FROM scratch
```

### ARG
```
ARG  CODE_VERSION=latest
FROM base:${CODE_VERSION}
...
FROM extras:${CODE_VERSION}
```

### RUN
Выполняется во время построения ОБРАЗА (в отличие от CMD)
```
RUN mkdir -p /var/lib/postgresql/data
RUN chown -R postgres:postgres /var/lib/postgresql/
```

### USER
Смена root на другого юзера:
```
USER postgres
USER user:group
```

### CMD
Запускает команду во время запуска КОНТЕЙНЕРА (в отличие от RUN)
```
CMD echo "This is a test." | wc -                    # выполняется в /bin/sh -c 
CMD ["/usr/bin/wc","--help"]
CMD ["/docker-entrypoint.sh"]
```

### ENTRYPOINT
Снова запуск команды во время запуска КОНТЕЙНЕРА (есть нюансы использования с CMD)
```
ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-h"]
```

### WORKDIR
Рабочая директория, откуда будут запускаться команды ENTRYPOINT и CMD
```
WORKDIR /opt/webapp/db
RUN bundle install
WORKDIR /opt/webapp
ENTRYPOINT ["rackup"]
```

### VOLUME
Добавление тома (директории) в образ
```
VOLUME ["/opt/project"]
```

### ADD vs COPY
- ADD
    - когда нужно загрузить ресурс из сети
    - когда нужно при копировании распаковать (не .zip) архив
    - ⚠️ распаковывает, только если архив находится в одной папке с Dockerfile
    - ⚠️ если выполняется скачивание - разархивирования не будет
- COPY
    - во всех остальных случаях

### EXPOSE
Проброс порта для документации
```
EXPOSE 8000
```

### LABEL
```
LABEL <key>=<value> <key>=<value> <key>=<value> ...
```

### ONBUILD
Добавляет тригеры в образы. Триггер исполняется, когда образ используется как базовый для другого образа, например, когда исходный код, нужный для образа еще не доступен, но требует для работы конкретного окружения.
```
ONBUILD ADD . /app/src
ONBUILD RUN cd /app/src && make
```

### STOPSIGNAL
Отправка сигнала для завершения работы 
```
STOPSIGNAL signal     # signal -  число соотв. таблице системных вызовов ядра (например, 9) или строка в формате SIGNAME (например SIGKILL)
```

### HEALTHCHECK
```
HEALTHCHECK [OPTIONS] CMD command   # проврека состояния контейнера командой внутри этого контейнера
HEALTHCHECK NONE                  # отключение всех базовых (унаследованных) проверок

HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
```

### SHELL
Переопределение дефолной оболочки
```
SHELL ["powershell", "-command"]
RUN Write-Host hello
...
SHELL ["cmd", "/S", "/C"]
RUN echo hello
```



