# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```

### Crear un volumen tipo host con la imagen nginx:alpine, para la ruta carpeta host: directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html esta ruta se obtiene al revisar la documentación
![Volúmenes](imagenes/volumen-host.PNG)
```
docker run -d --name mi-contenedor -v D:\Docker\Construction\Practice3\nginx\html:/usr/share/nginx/html -p 80:80 nginx:alpine
```
### ¿Qué sucede al ingresar al servidor de nginx?

Al acceder al servidor nginx mediante `localhost`, aparece un código de estado HTTP "403 Forbidden", que indica que no existe permiso para acceder al recurso solicitado. En otras palabras, el servidor ha entendido la solicitud, pero está denegando el acceso debido a restricciones de autenticación o autorización.

### ¿Qué pasa con el archivo index.html del contenedor?

El archivo index.html no está presente, lo que causa el error 403.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de nginx/html
### ¿Qué sucede al ingresar al servidor de nginx?

Al ingresar al servidor de nginx, se muestra la página resultante de los archivos descomprimidos del template seleccionado.

### Eliminar el contenedor
```
docker rm -f mi-contenedor
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?

Dado que ya existe un archivo index.html al ejecutar

```
docker run -d --name mi-contenedor -v D:\Docker\Construction\Practice3\nginx\html:/usr/share/nginx/html -p 80:80 nginx:alpine
```

al acceder al `localhost`, ya aparece la pagina cargada con el template antes seleccionado.

### ¿Qué hace el comando pwd?
El comando pwd en sistemas UNIX y derivados, como Linux, muestra el directorio de trabajo actual en la consola.

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

