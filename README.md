# Docker · Apache 2 · PHP-FPM 7.4 · MySQL 8

// Customize your docker compose env vars

cp docker-compose.override.yml.dist docker-compose.override.yml
// Start the containers

docker-compose up
// Initialize composer

docker-compose exec php-fpm composer init
// Install dependencies

docker-compose exec php-fpm composer install
// Test MySQL server connection

docker-compose exec mysql mysql -uroot -ppfm
//
