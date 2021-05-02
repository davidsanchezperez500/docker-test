# docker-test

## Configurar multi-container

1. Crear red
~~~
docker network create todo-app
~~~

2. Correr el contenedor MySQL
~~~
docker run -d \
--network todo-app --network-alias mysql \
-v todo-mysql-data:/var/lib/mysql \
-e MYSQL_ROOT_PASSWORD=secret \
-e MYSQL_DATABASE=todos \
mysql:5.7
~~~

3. Correr nuestro contenedor y que se conecte al de MySQL
~~~
docker run -dp 3000:3000 \
--network todo-app \
-e MYSQL_HOST=mysql \
-e MYSQL_USER=root \
-e MYSQL_PASSWORD=secret \
-e MYSQL_DB=todos \
getting-started
~~~



### Enlaces de interes
- https://hub.docker.com/_/mysql
