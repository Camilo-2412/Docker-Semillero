Imagenés
====
Una imagen es una plantilla de solo lectura con instrucciones para crear un contenedor Docker.

A menudo, una imagen se basa en otra imagen, con alguna personalización adicional. Por ejemplo, puede crear una imagen basada en la imagen de ubuntu, pero a su vez instalar el servidor web Apache y sus aplicaciones, así como los detalles de configuración necesarios para que su aplicación se ejecute.

NGINX
===
Nginx  es un servidor proxy inverso de código abierto para los protocolos HTTP, HTTPS, SMTP, POP3 e IMAP, así como un equilibrador de carga, una caché HTTP y un servidor web (servidor de origen). El proyecto nginx comenzó con un fuerte enfoque en la alta concurrencia, el alto rendimiento y el bajo uso de memoria. Tiene una licencia de tipo BSD de 2 cláusulas y funciona en Linux, variantes BSD, Mac OS X, Solaris, AIX, HP-UX, así como en otros sabores de *nix. También tiene una prueba de concepto para Microsoft Windows.

Usar una imagen de Nginx para hostear una página de contenido estático simple.
===
1. Crear una carpeta en nuestra máquina virtual e ingresar a ella.

```linux=
mkdir mi-primer-dockerfile/
cd mi-primer-dockerfile/
```
2. Crear el archivo ```Dockerfile``` y agregar las  siguientes lineas.

```linux=
FROM nginx
COPY static-html-directory /usr/share/nginx/html
```

3. Crear un directorio llamado ```static-html-directory``` haciendo referencia a las lineas que ingresamos en el paso anterior.
```linux=
mkdir static-html-directory
```

4. Creamos un archivo html ```index.html``` con contenidoa nuestro gusto, y probamos que todo está correcto.

```linux=
vim index.html
cat index.html
```

5. Construimos la imagen dentro del directorio ```mi-primer-dockerfile```.
```linux=
docker image build -t some-content-nginx .
```

6. Correr la imagen en el puerto ```8080```.

```linux=
docker run --name some-nginx -d -p 8080:80 some-content-nginx
```

7. Probar que la imagen está corriendo satisfactoriamente.

```linux=
curl -k localhost:8080
```

Algunos comandos a tener en cuenta
===
 Ver las imagenes que tenemos.
 
 ```linux=
 docker image ls
 ```
 
 Ver los contenedores.
 
 ```linux=
 docker ps -a
 ```
 
 Para eliminar una imagen.
 ```linux=
 docker rmi image "IMAGE_ID"
 ```
 
 Eliminar contenedor.
 ```linux=
 docker rm "CONTAINER_NAME or CONTAINER_ID"
 ```
 
 Detener contenedor.
  ```linux=
 docker stop "CONTAINER_NAME or CONTAINER_ID"
 ```
 
 
 Docker Hub
 ===
 
 Para poder linkear tu cuenta de docker hub con tu máquina virtual.
 
 ```linux=
 docker login
 ```
 
 Te pedirá tus credenciales de Docker Hub.
 
 Para subir una imagen desde tu máquina a tu Docker Hub creando un repositorio.
 
```linux=
docker tag "nombre de tu imagen"  "usuario"/"nombre del repo "
docker push  "usuario"/"nombre del repo"
```

Para traer una imagen desde otro repositorio

```linux=
docker pull  "usuario"/"nombre del repo"
```

Link de la imagén subida en clase:
https://hub.docker.com/repository/docker/camilo2412/fedesoft-web