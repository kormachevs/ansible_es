Написать ansible playbook для развертывания 3-нодового кластера elasticsearch. 
Не имеет значения в контейнере будут инстансы или нет. Прислать playbook с комментариями, описывающими его работу.

    ###Комментарии:

ansible-playbook elasticsearch.yaml -l es

1. Установка зависимостей: java , apt-transport-https
2. Добавление ключа GPG
3. Добавление репозитория elasticsearch
4. Установка elasticsearch
5. Копирование измененного elasticsearch.service, т.к сервис не успевал стартануть и systemd его останавливал.
    Добавил TimeoutSec=900;
6. Копирование конфигурации на каждую ноду из шаблона.

PS: master_node, data_node_1, data_node_2, должны быть прописаны в DNS или добавлены в hosts на каждой машине кластера.
___
Опционально: опишите словами - какие минимальные правки нужно внести в данный playbook, чтобы обеспечить его корректное выполнение в случае, если с целевых хостов нет выхода в интернет, а есть только с хоста, на котором выполняется ansible, при этом доступ осуществляется через корпоративный прокси сервер.

Для каждой задачи, которой нужен интернет использовать environments, в которой будет описан https_proxy.
