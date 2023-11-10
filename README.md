# docker_task
docker assignments in devops course

Задание 1.1
В папке nginxtask создаем файл nginx.conf в котором прописываем возможность запрета POST запросов.
для этого нам потребуется сначала запустить контейнер командой (естественно образ nginx:alpine я предварительно загрузил и назвал его nginx:alpine):

  docker run --rm -d --name nginx nginx:alpine

а потом выполнить команду:

  docker cp nginx:/etc/nginx/nginx.conf nginx.conf

ну или банально подключиться к контейнеру с параметром sh найти его через командную строку выведя содержимое в консоль через терминал и скопировав 

  docker exec -it nginx sh

Далее мы добавляем в файл nginx.conf возможность запрета POST запросов и пишем Dockerfile, который соберет необходимую конструкцию

Все команды запускаем из директории
Собираем командой
docker build -t _______ .

Запускаем командой в фоновом режиме с пробросом портов
docker run -d -p 80:80 __________

Задание 1.2

docker build -t ________ .

Запускаем командой
docker run --name _________ -e POSTGRES_PASSWORD=password -d student04_1_2

Заходим внутрь контейнера от пользователя test
docker exec -it student04_pdb psql -U test

командами \du \l проверяем список пользователей и список баз данных и убеждаемся о наличии
