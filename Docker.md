# Docker - Команди

[Сайт](https://docs.docker.com/engine/reference/commandline/docker/)

1. [`docker ps`](https://docs.docker.com/engine/reference/commandline/ps/)

   - `docker ps` - виводить список **запущених** контейнерів.
   - `docker ps -q` - команда виводить тільки **id** контейнерів (корисно, коли вам потрібно знати тільки id або використовувати цю команду в сценаріях).
   - `docker ps -a` - показує всі контейнери, а не тільки запущені.

2. [`docker pull`](https://docs.docker.com/engine/reference/commandline/pull/) - завантаження образу.

3. [`docker build`](https://docs.docker.com/engine/reference/commandline/build/) - збирає образ.

   - `docker build -t sergiokapone/name .` - збирає образ з поточного каталогу (`.`).

4. [`docker volume ls`](https://docs.docker.com/engine/reference/commandline/volume_ls/) - список томів.

   Дана команда показує список томів, які є основним механізмом для зберігання даних, що генеруються контейнерами Docker.
   

5. [`docker images`](https://docs.docker.com/engine/reference/commandline/images/) - список образів, які ви маєте на локальній машині.

   - `docker images --format "{{json .}}"` - відображає список образів в форматі JSON, що може бути корисним для автоматичної обробки виводу.
   - `docker images --format "{{.Repository}}"` - команда відображає тільки імена репозиторіїв образів без додаткової інформації.
   - `docker images --filter "dangling=false"` - відображає тільки активні шари образів і виключає не використовувані (повісні) шари.

6. [`docker run`](https://docs.docker.com/engine/reference/commandline/run/) - запуск контейнера.

   - `docker run sergiokapone/name` - запускає контейнер на основі образу `sergiokapone/name` з використанням налаштувань за замовчуванням.
   - `docker run -p 8080:80 sergiokapone/name` - контейнер буде запущений, і порт `80` всередині контейнера буде прив'язаний до порту `8080` на хостовій машині. Таким чином, при доступі до порту 8080 на хостовій машині буде встановлено з'єднання з портом `80` всер
     ередині контейнера.
   - `docker run -v /path/on/host:/path/in/container sergiokapone/name` - контейнер буде запущений, і каталог `/path/on/host` на хостовій машині буде змонтований як `/path/in/container` всередині контейнера. Це дозволяє обмінюватись даними між хостовою машиною і контейнером.
   - `docker run -d sergiokapone/name` - контейнер буде запущений у фоновому режимі (режим демона), що означає, що команда `docker run` виконуватиметься у фоновому режимі, і ви отримаєте зворотний контроль над командним рядком.
   - `docker run -e VAR_NAME=value sergiokapone/name` - змінна оточення `VAR_NAME` буде встановлена на значення `value` всередині контейнера. Ви можете використовувати цей метод для передачі налаштувань або конфігурації до контейнера.
   - `docker run -it sergiokapone/name bash` - інтерактивний режим.

7. [`docker logs`](https://docs.docker.com/engine/reference/commandline/logs/) - перегляд логів.

   Дозволяє переглянути логи вказаного контейнера. Можна використовувати прапорець `-follow`, щоб слідкувати за логами працюючого контейнера, наприклад, `docker logs -follow sergiokapone/name`.

8. [`docker stop`](https://docs.docker.com/engine/reference/commandline/stop/) - зупинка контейнера.

   Використовується для "м'якого" зупинення контейнера.

9. [`docker kill`](https://docs.docker.com/engine/reference/commandline/kill/) - "вбивство" контейнера.

   Не намагається коректно завершити процес, подібно до системної команди `kill`.

10. [`docker container prune`](https://docs.docker.com/engine/reference/commandline/container_prune/) - видалити всі зупинені контейнери в Docker.

11. [`docker image prune`](https://docs.docker.com/engine/reference/commandline/image_prune/) - видалити всі невикористані контейнери в Docker.

12. [`docker rm`](https://docs.docker.com/engine/reference/commandline/rm/) - видалити контейнер.

13. [`docker rmi`](https://docs.docker.com/engine/reference/commandline/rmi/) - видалити образ.

14. [`docker system prune`](https://docs.docker.com/engine/reference/commandline/system_prune/) - видалити невикористані контейнери, образи, томи та мережі, звільняючи простір на диску.
    - `docker system prune --all` - видалити всі контейнери, образи, томи та мережі, включаючи ті, які використовуються. Усі дані будуть безповоротно видалені.
