# Задание 1.1
В папке nginx_task создаем файл nginx.conf в котором прописываем возможность запрета POST запросов.
для этого нам потребуется сначала запустить контейнер командой (естественно образ nginx:alpine я предварительно загрузил и назвал его nginx:alpine):

    docker run --rm -d --name nginx nginx:alpine

а потом выполнить команду:

    docker cp nginx:/etc/nginx/nginx.conf nginx.conf

ну или банально подключиться к контейнеру с параметром sh найти его через командную строку выведя содержимое в консоль через терминал и скопировав 

    docker exec -it nginx sh

Далее мы добавляем в файл nginx.conf возможность запрета POST запросов и пишем Dockerfile, который соберет необходимую конструкцию

Все команды запускаем из директории в которой находтся файлы Dockerfile и nginx.conf
Собираем командой:

    docker build -t my_nginx:1 .

Запускаем командой в фоновом режиме с пробросом портов:

    docker run -d -p 80:80 my_nginx:1

или просто для проверки работы с отслеживанием в консоли:

    docker run -it -p 80:80 my_nginx:1

# Задание 1.2

Возможны два варианта решения данного задания. В первом мы используем Dockerfile который заберет с hub.docker.com образ latest и переменными окружения задаст пользователя и базу, сборка по вот этой команде:

    docker build -t my_postgres .

Запускаем командой:

    docker run --name test_postgres -e POSTGRES_PASSWORD=testpassword -d -p 5432:5432 my_postgres

или с volume:

    docker run --name test_postgres -e POSTGRES_PASSWORD=testpassword -d -v custom-postgres-data:/var/lib/postgresql/data my_postgres

Пароль мы специально не задаем в образе это считается дурным тоном, а передаем при запуске контейнера, эта переменная окружения является обязательной

Заходим внутрь контейнера от пользователя test:

    docker exec -it test_postgres psql -U test

Проверить наличие пользователя мы можем командой:

    \du

Проверить налицие базы данных мы можем командой:

    \l

Ну и стандартная проверка:

    SELECT 1;

Для удобства работы можно сразу же поднять контейнер с apsche superset:

    docker run -d -p 8080:8088 -e "SUPERSET_SECRET_KEY=your_secret_key_here" --name superset apache/superset
    
    docker exec -it superset superset fab create-admin \
              --username admin \
              --firstname Superset \
              --lastname Admin \
              --email admin@superset.com \
              --password admin

    docker exec -it superset superset db upgrade

    docker exec -it superset superset init

Подключение  http://localhost:8080/login/ -- u/p: [admin/admin]


Второй способ связан с созданием файла init.sql этот образ сохранен в файле Dockerfile2 для него можно иcпользовать следующие команды запуска:

    docker build -f Dockerfile2 C:\Users\pavel\docker_tasks\Postgres -t mypostgres2
    docker run -d --name mypostgres2 -p 5432:5432 mypostgres2 
    docker start mypostgres2
    docker exec -it mypostgres2 psql -U test

Но первый способ кажется мне гораздо приятнее и проще


