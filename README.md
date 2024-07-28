# Домашнее задание к занятию 10 «Jenkins» - `Мурчин Артем`

## Подготовка к выполнению

1. Создать два VM: для jenkins-master и jenkins-agent.
2. Установить Jenkins при помощи playbook.
3. Запустить и проверить работоспособность.
4. Сделать первоначальную настройку.

## Решение - подготовка к выполнению

Создал два VM: для jenkins-master и jenkins-agent.

![alt text](https://github.com/artmur1/19-04-jenkins-hw/blob/main/img/19-04-01-00-hw.png)

Плейбук завершен с ошибкой - не удается скачать agent.jar.

![alt text](https://github.com/artmur1/19-04-jenkins-hw/blob/main/img/19-04-01-02-hw.png)

Подключился к ВМ jenkins-master, оказывается jenkins не запущен. Пробую запустить - не удается.

![alt text](https://github.com/artmur1/19-04-jenkins-hw/blob/main/img/19-04-01-03-hw.png)

    ● jenkins.service - Jenkins Continuous Integration Server
       Loaded: loaded (/usr/lib/systemd/system/jenkins.service; enabled; vendor preset: disabled)
       Active: failed (Result: start-limit) since Sun 2024-07-28 10:07:37 UTC; 1s ago
      Process: 4931 ExecStart=/usr/bin/jenkins (code=exited, status=1/FAILURE)
     Main PID: 4931 (code=exited, status=1/FAILURE)
    
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: jenkins.service: main process exited, code=exited, status=1/FAILURE
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: Failed to start Jenkins Continuous Integration Server.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: Unit jenkins.service entered failed state.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: jenkins.service failed.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: jenkins.service holdoff time over, scheduling restart.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: Stopped Jenkins Continuous Integration Server.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: start request repeated too quickly for jenkins.service
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: Failed to start Jenkins Continuous Integration Server.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: Unit jenkins.service entered failed state.
    Jul 28 10:07:37 centos7-jm.ru-central1.internal systemd[1]: jenkins.service failed.

Запускаю плейбук из задания стандартный, никаких изменений не вносил. Сервис jenkins не запускается потому что я что-то не правильно делаю, либо из-за того, что Centos7 больше не поддерживается?

## Основная часть

1. Сделать Freestyle Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
2. Сделать Declarative Pipeline Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
3. Перенести Declarative Pipeline в репозиторий в файл `Jenkinsfile`.
4. Создать Multibranch Pipeline на запуск `Jenkinsfile` из репозитория.
5. Создать Scripted Pipeline, наполнить его скриптом из [pipeline](./pipeline).
6. Внести необходимые изменения, чтобы Pipeline запускал `ansible-playbook` без флагов `--check --diff`, если не установлен параметр при запуске джобы (prod_run = True). По умолчанию параметр имеет значение False и запускает прогон с флагами `--check --diff`.
7. Проверить работоспособность, исправить ошибки, исправленный Pipeline вложить в репозиторий в файл `ScriptedJenkinsfile`.
8. Отправить ссылку на репозиторий с ролью и Declarative Pipeline и Scripted Pipeline.
9. Сопроводите процесс настройки скриншотами для каждого пункта задания!!

## Необязательная часть

1. Создать скрипт на groovy, который будет собирать все Job, завершившиеся хотя бы раз неуспешно. Добавить скрипт в репозиторий с решением и названием `AllJobFailure.groovy`.
2. Создать Scripted Pipeline так, чтобы он мог сначала запустить через Yandex Cloud CLI необходимое количество инстансов, прописать их в инвентори плейбука и после этого запускать плейбук. Мы должны при нажатии кнопки получить готовую к использованию систему.

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
