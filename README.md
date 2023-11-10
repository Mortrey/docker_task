# docker_task
docker assignments in devops course

Задание 1.1
В папке ngin создаем файл nginx.conf в котором прописываем возможность запрета POST запросов. Все команды запускаем из директории
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
