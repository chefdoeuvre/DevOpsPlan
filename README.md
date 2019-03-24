# DevOpsPlan
<b>To do</b><br/>
[v] simple python+flask application<br/>
[v] put project in docker container via docker build+Dockerfile<br/>
[v] jenkins with simple task <br/>
[o] move jenkins from Kasumi to Haruna (docker?) <br/>
[o] move project in docker to aws <br/>
[o] start project on aws only in use. via jenkins? <br/>
[o] configure webhooks on github<br/>
[o] project rebuild, if new commit, and restart docker container if necessary (aws+jenkins+docker-no balance) <br/>
[o] unit test in jenkins? more stages? <br/>
[o] mb it's time to add postgresql to project? just for fun <br/>

[next steps...] <br/>

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
