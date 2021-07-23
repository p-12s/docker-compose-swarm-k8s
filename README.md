![License](https://img.shields.io/github/license/p12s/2gis-catalog-api)

## ⭐️ Docker  
*приложение с его зависимостями, упакованное в процесс (окружение)*  
#### Принцип работы
- Namespaces
  - Изоляция окружения
  - Индивидуальный namespace для каждого контейнера: PID, net, mount, etc.
  - Namespace прекращает свое существование после окончания работы PID=1
- Cgroups
  - Использование контейнерами обоих ресурсов
  - Ограничение ресурсов
  - CPU, memory, IO, etc.
- Docker UnionFS
- RunC
#### Что можно поизучать дополнительно
- попробовать поработать с containerd - можно поднимать процесс и без докера
-----------

## ✨✨ Docker-compose

#### Где использовать в 202x
- Локальная разработка, когда используется связка сервисов
-----------

![orchestration](https://github.com/p-12s/docker-compose-swarm-k8s/blob/main/orchestration.jpg?raw=true)
## Docker-swarm (k8s для бедных)

#### Где использовать в 202x
- Локальная разработка, при которой нужен скейлинг
- Stage/prod небольших проектов (от 1 и более виртуальных машин)

#### Почему использовать в 202x
- он проще по-сравнению с minikube/k8s
- поддерживает скейлинг сервисов (контейнеров)
- скачивание образов при запуске в стеке, автоподнятие упавших сервисов (контейнеров)
- поддерживает секреты (secrets)
-----------

## 🔥🔥 Minikube (поиграться с k8s на локале)

#### Где использовать в 202x
- Локальная разработка, когда прод на k8s
- минимальный принципиально-полный функционал
-----------

## ⚡️⚡️⚡️ Kubernetes

#### Почему для большого Enterprise
- большие возможности кастомизации
- готовые решения в облаке
- сильная экспертиза разработчиков

