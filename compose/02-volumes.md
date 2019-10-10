Volumes
===================

Your application lives only as long as its containers remain running. To make data storage persistent, you have to use volumes.

How? Nothing changes here:

```
docker-compose up -d
```

But docker-compose.yml has slightly changed:

## docker-compose.yml
```
version: '3.5'

services:
  db:
    image: drupaldocker/mariadb:10.3
    environment:
      MYSQL_ALLOW_EMPTY_PASSWORD: 'True'
    volumes:
      - db_volume:/var/lib/mysql
  cli:
    image: drupaldocker/php:7.0-cli-2.x
    links:
      - db
    volumes:
      - file_volume:/var/www/html

volumes:
  db_volume:
  file_volume:
```
