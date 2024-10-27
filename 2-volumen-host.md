# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)
```
docker run -d --name my_nginx -p 8080:80 -v "C:/Users/marlo/Desktop/EPN 2024-B/Construccion/Practica3/nginx/html:/usr/share/nginx/html" nginx:alpine
```

### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar a la direccion http://localhost:8080/ se puede observar que muestra el contenido de la carpeta html, misma que se encuentra vacia.

### ¿Qué pasa con el archivo index.html del contenedor?
Sea el caso de tener un index.html el contenido deberia mostrarse en la direccion que hemos abierto.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Una vez hemos descargado el template gratuito y lo hemos descomprimido en la carpeta html, es importante que los archivos esten en html y no en otra carpeta. Se llega a observar que el servidor despliega el contenido del index.html con todos sus secciones e imagenes.

### Eliminar el contenedor
```
docker rm -f my_nginx
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
Una vez mediante el comando anterior se ha eliminado el contenedor y al volverlo a crear se llega a observar que la informacion se vuelve a mostrar, es decir, el template de HTML5 se muestra tal cual estaba antes de eliminarlo.

### ¿Qué hace el comando pwd?
El comando pwd significa "Print Working Directory" y genera la ruta absoluta del directorio en el que se encuentra.
Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

