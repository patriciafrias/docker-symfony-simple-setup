# Docker · Apache 2 · PHP-FPM 7.4 · MySQL 8

#### Customize your docker compose env vars:
```cp docker-compose.override.yml.dist docker-compose.override.yml```

#### Start the containers:  
```docker-compose up```


#### Install dependencies:  
```docker-compose exec php-fpm composer install```


#### Test MySQL server connection:  
```docker-compose exec mysql mysql -uroot -ppfm```

#### Test the web server:
http://localhost/

You will see the Symfony start page
