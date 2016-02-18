## Basic Usage
```
docker run --name suitecrm \
-e DATABASE_NAME=thedbname \
-e DB_TYPE=mysql \
-e DB_MANAGER=MysqlManager \
-e DB_HOST_NAME=thedbhost \
-e DATABASE_NAME=thedbname \
-e DB_USER_NAME=theusername \
-e DB_PASSWORD=thepassword \
-d afallison/docker-suitecrm suitecrm
```

## Advanced Usage
```
# Build MariaDB container
docker run --name mariadb -v /custom-folder/mariadb:/var/lib/mysql -e MYSQL_ROOT_PASSWORD="thepassword" -d mariadb

# Build Nginx
docker run -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock:ro jwilder/nginx-proxy

# Build Redis
docker run --name redis -d redis

# Build it
docker run --name suitecrm \
--link redis:redis \
--link mariadb:mysql \
-v /custom-folder:/var/www/html \
-e DATABASE_NAME=thedbname \
-e DB_TYPE=mysql \
-e DB_MANAGER=MysqlManager \
-e DB_HOST_NAME=thedbhost \
-e DATABASE_NAME=thedbname \
-e DB_USER_NAME=theusername \
-e DB_PASSWORD=thepassword \
-e VIRTUAL_HOST=www.mysuitedomain.net \
-d afallison/docker-suitecrm suitecrm

```
---

Thanks to original build from: https://github.com/Spantree/docker-suitecrm