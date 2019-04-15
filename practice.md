# DevOpsPlan
<b>small practice jenkins+flask+python (Debian)+docker</b><br/>
[v] simple python+flask application<br/>
[v] put project in docker container via docker build+Dockerfile<br/>
[v] jenkins with simple task <br/>
[v] move jenkins from Kasumi to Haruna (docker?) <br/>
[v] configure webhooks on github<br/>
[v] project rebuild, if new commit, and restart docker container if necessary (jenkins+docker-no balance)<br/>
<hr/>
<b>AWS+puppet/ansible</b> <br/>
[v] AWS configuration/credentials/Ec2InstanceMetadata/roles(IAM)/vpc/subnets/route table and etc
[v] practice w/ creating and manage hosts (instances) via AWS CLI <br/>
[v] 1 aws amazon, 1 mgmt for puppet/ansible server (ubuntu again), 2 ubuntu srvrs as clients <br/>
[v] practice w/ ansible/ansible-playbook/raw commands<br/>
[~] practice w/ puppet \0/ -- later <br/>
<hr/>
<b>GCP+Kubernetes/kubectl (GKE)</b> <br/>
[v] gcloud CE, cli, kubectl, pods\deployment\service\cluster\etc. <br/>
[v] Ingress(Service(deployment(docker image(flask+python)))) %_% <br/>
[o] in progress.. <br/>
<hr/>
DB:
[v] Nginx<br/>
[v] Docker repeat <br/>
[v] nginx -> var/log -> filebeat -> kafka, completed <br/>
[v] Grafana, try. <br/>
[~] Jenkins: local git-jenkins-nginx <br/>

<br/>(heroku,prometheus,k8s,chef, azure, helm)<br/>

<hr/>
План-шаблон, чтобы не потерять:

Сразу напишем небольшое приложение. Язык выбираем абсолютно любой. Приложение будет отдавать информацию о пользователях через HTTP. По сути, простенькое API.
Теперь давайте добавим работу с базой: пусть наши пользователи хранятся в базе. Идеально структуру базы хранить рядом с кодом и научиться прогонять миграции при новых изменениях. Таким образом ваше приложение само синхронизирует базу до нужной структуры.
Регистрируемся на github.com/bitbucket.org и закидываем весь исходный код нашего приложения туда.
На своей машине поднимаем jenkins/teamcity и настраиваем автоматическую сборку приложения из нашего репозитория по кнопке.
Усложняем задачу. Настроим webhooks на github/bitbucket, которые будут автоматически запускать сборку на jenkins/teamcity.
Добавим тестов в jenkins: как минимум можно прогонять lint по нашему коду или набросать unit тесты.
Переключимся на настройку dev окружения. Берем в руки ansible/chef/puppet/salt и настраиваем виртуалку с нуля: создаем пользователей, устанавливаем необходимые библиотеки и зависимости.
Подводим все это дело под vagrant: виртуалка должна автоматически подниматься и настраиваться.
Подключаем vagrant к jenkins с помощью соответствующего плагина: при пуше в git наше приложение собирается, и поднимается виртуальное окружение с помощью vagrant + configuration system management.
Ищем best practices по деплою приложений на языке, который вы выбрали. Можно заворачивать все в deb/rpm пакеты, можно деплоить ruby с помощью capistrano. Главное — выбрать решение.
Выбор сделан, реализуем его и конфигурируем jenkins, чтобы после пуша в репозиторий, jenkins, помимо сборки приложения и развертывания окружения, выкладывал и запускал наш код.
Добавляем смоук тесты: после запуска jenkins должен запросить список пользователей у нашего API и убедиться, что получает ответ.
Добавляем мониторинг нашего проекта: изучаем time series базы, настраиваем prometheus, grafana, автоматически подключаем новый инстанс нашего приложения к мониторингу.
Улучшаем мониторинг: интегрируемся со slack и pagerduty, чтобы получать нотификации.
Читаем про докер, пишем Dockerfile и оборачиваем наше приложение.
Изучаем увлекательные статьи про настройку систем оркестрации swarm, kubernetes, rancher cattle. Следуем рекомендациям и поднимаем кластер.
Меняем Jenkins: собираем docker образ, прогоняем тесты, запускаем собранный докер на кластере kubernetes, проводим smoke тесты, вводим наше приложение в балансировку.
