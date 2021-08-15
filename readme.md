Эта команда поднимает ваши контейнеры, но перед этим запускает сборку
(--build) и запускает ваши контейнеры в режиме демона (-d)

docker-compose up --build -d

после тоого, как в консоли увидели напротив каждого образа .... done
можно проверить, всё ли работает, перейдя по ссылке

localhost:8081 
должен открыться файл app/public/index.php

localhost:8080
тут должен открыться phpMyAdmin

Если все прошло хорошо, давайте установим Symfony в нашу папку app. 
Заходим в наш контейнер с php-cli: 

docker exec -it symfony-app-php-cli bash

В контейнере выполняем следующую команду, чтобы установить Symfony: 

composer create-project symfony/website-skeleton app

После установки выполняем несколько команд, чтобы избавиться от вложенности папок:

mv /symfony/app/* /symfony
mv /symfony/app/.* /symfony
rm -Rf app

Теперь пробуйте открыть localhost:8081, 
вас должна приветствовать свежая версия Symfony