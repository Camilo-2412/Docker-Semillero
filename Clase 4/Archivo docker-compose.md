Archivo docker-compose
==

1. Crear carpeta ```proxy```.

```=
mkdir proxy
```
2. Crear archivo ```docker-compose.yml``` y agregar las siguientes lineas.

```linux=
version: '3'
services:
  web:
    image: dockercloud/hello-world
  lb:
    image: dockercloud/haproxy
    links:
      - web
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 80:80
```

3. Levantar el contenedor.

```=
docker-compose up -d
```

4. Listar contenedores.

```=
docker-compose ps
```


Otros comandos a tener en cuenta.
==

Ver info de los contenedores

```=
docker info
```

Dar de baja a los contenedores.
```=
docker-compose down
```

Dar escalabilidad creado varios conrtenedores que responden las peticiones.
```=
docker-compose up --scale "servicio"=#contenedores -d
```

Instalar yJenkins.
==

1. Bajar el repositorio.
```=
git clone https://github.com/jsgiraldoh/Jenkins.git
```

2. Levantar el servicio (debido a que el .yml no tiene el nombre estandar, se informa con la banderilla -f y el nombre del archivo .yml cual es el nombre de este archivo)
```=
docker-compose -f docker-compose-jenkins.yml up -d
```
3. Se establece usuario propietario.
```=
sudo chown ubuntu:ubuntu jenkins_home/
```

4. Se establecen permisos.
```=
sudo chmod 2777 jenkins_home/
```

5. Se mira la contraseña generada para Jenkis.
```=
docker log
```

6. Dirigirse a la ip ```ip:8090``` y se logea con la clave necesaria, y se finaliza la instalación.


