Instalación de Docker en Ubuntu
==
Antes de instalar el motor Docker por primera vez en una nuevo host, es necesario configurar el repositorio Docker. Después, puedes instalar y actualizar Docker desde el repositorio.

1. Actualizar el índice de paquetes apt e instalar paquetes para permitir que apt utilice un repositorio a través de HTTPS:

``` linux=
apt-get update
```

2. Instale paquetes para permitir el uso de un repositorio sobre HTTPS.

``` linux=
 sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```


3. Añadir la clave GPG oficial de Docker

``` linux=
 echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Instalar Motor Docker
===

1. Actualiza el índice de paquetes apt, e instala la última versión de Docker Engine y containerd

``` docker=
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
``` 

2. Verifique que el motor Docker está instalado correctamente ejecutando la imagen hello-world.

``` docker=
sudo docker run hello-world
``` 


Instalar Docker Compose
===

En Linux, puedes descargar e Docker Compose desde la página de lanzamiento del repositorio de Compose en GitHub.

1. Ejecute este comando para descargar la versión estable actual de Docker Compose:


``` linux=
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
``` 

2. Aplicar permisos de ejecución al binario:


``` linux=
sudo chmod +x /usr/local/bin/docker-compose
```

3. Probar la instalación: 
``` linux=
 docker-compose --version
```

Algunos comandos:
===

Crear e iniciar contenedores:

``` linux=
sudo docker-compose up -d
```


Lista contenedores corriendo:

``` linux=
sudo docker container ls
```

Detener contenedores corriendio:

``` linux=
sudo systemctl stop docker
```

Establecer que siempre que la maquina inicie, arranque los contenedores automáticamente. 
``` linux=
 sudo systemctl enable docker
```

Agregar usuario:
``` linux=
sudo usermod -aG docker usuario
```

Ver log:
``` linux=
docker logs -f
```

Detener o iniciar contenedores: 
``` linux=
docker container stop 
docker container start 523811282c26
```