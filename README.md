добавим в /etc/hosts:
<p style="color: #F8F8F8; font-weight: bold;">  127.0.0.1	laravel8.org</p>

выполним:
<p style="color: #F8F8F8; font-weight: bold;"> git clone [имя этого репозитоия] laravel8.org </p>
<p style="color: #F8F8F8; font-weight: bold;"> cd laravel8.org </p>
<p style="color: #F8F8F8; font-weight: bold;"> cp application/.env.example application/.env </p>

настроим содержимое .env:

    APP_NAME=MY
    DB_HOST=db
    DB_PORT=3306
    DB_DATABASE=db_name
    DB_USERNAME=db_username
    DB_PASSWORD=db_password
	APP_URL=https://laravel8.org

далее:
<p style="color: #F8F8F8; font-weight: bold;">
docker-compose  --env-file ./application/.env up  -d --build
</p>

<p style="color: #F8F8F8; font-weight: bold;">
docker-compose exec app composer install
</p>

<p style="color: #F8F8F8; font-weight: bold;">
docker-compose exec app php artisan key:generate
</p>

далее вместо того чтобы каждый раз писать <span  style="color: #F8F8F8; font-weight: bold;">docker-compose exec app</span> можно использовать для входа в контейнер:
<p style="color: #F8F8F8; font-weight: bold;">
docker exec -it laravel-app bash
</p>

должены быть выполнены миграции и посев данных:
<p style="color: #F8F8F8; font-weight: bold;">
php artisan migrate --seed
</p>
