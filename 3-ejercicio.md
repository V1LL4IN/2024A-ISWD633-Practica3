## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es /var/lib/mysql.

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?

La carpeta db del host contendrá todos los archivos y directorios necesarios para almacenar los datos de la base de datos MySQL

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO

```
docker run -d --name mysql-container --network net-wp \
    -e MYSQL_ROOT_PASSWORD=myrootpassword \
    -e MYSQL_DATABASE=mydatabase \
    -e MYSQL_USER=myuser \
    -e MYSQL_PASSWORD=mypassword \
    -v $(pwd)/ejercicio3/db:/var/lib/mysql \
    mysql:8

```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Después de ejecutar el contenedor MySQL, la carpeta db ahora contiene los archivos y directorios que MySQL utiliza para almacenar la base de datos.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/

En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html.

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
```
docker run -d --name wordpress-container --network net-wp \
    -e WORDPRESS_DB_HOST=mysql-container:3306 \
    -e WORDPRESS_DB_USER=myuser \
    -e WORDPRESS_DB_PASSWORD=mypassword \
    -e WORDPRESS_DB_NAME=mydatabase \
    -v $(pwd)/ejercicio3/www:/var/www/html \
    -p 9500:80 \
    wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

<img width="1378" alt="image" src="https://github.com/V1LL4IN/2024A-ISWD633-Practica3/assets/135792941/eee4d4f0-3d1f-4d82-a4eb-4cdb70d2ddf0">


### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al eliminar y volver a crear el contenedor de WordPress usando el comando anterior, todas las personalizaciones y entradas agregadas persisten. Esto se debe a que el contenido de WordPress se ha almacenado en la carpeta del host www.



