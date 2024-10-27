## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
La carpeta db del host deberá contener los archivos de base de datos de MySQL, como archivos de tablas y demás archivos necesarios para su funcionamiento.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name my_mysql --network net-wp -e MYSQL_ROOT_PASSWORD=my_root_password -e MYSQL_DATABASE=my_database -e MYSQL_USER=my_user -e MYSQL_PASSWORD=my_password -v "C:\Users\marlo\Desktop\EPN 2024-B\Construccion\Practica3\ejercicio3\db:/var/lib/mysql" mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Una vez ejecute el comando, automaticamente la carpeta comenzo a llenarse de archivos y directorios de la base de Datos de MYSQL.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name my_wordpress --network net-wp -p 9500:80 -e WORDPRESS_DB_HOST=my_mysql:3306 -e WORDPRESS_DB_USER=my_user -e WORDPRESS_DB_PASSWORD=my_password -e WORDPRESS_DB_NAME=my_database -v "C:\Users\marlo\Desktop\EPN 2024-B\Construccion\Practica3\ejercicio3\www:/var/www/html" wordpress
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al recrear el contenedor de WordPress utilizando los mismos volúmenes asignados, tanto las configuraciones personalizadas como los datos previamente ingresados se conservan. Esto se debe a que la información se almacena en los directorios del host ```.../ejercicio3/www para WordPress y .../ejercicio3/db para MySQL``` los cuales permanecen intactos al eliminar los contenedores.



