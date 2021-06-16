# Comandos

## docker build

### Descripción

Construye una imagen desde un Dockerfile

### Uso

```bash
docker build [OPTIONS] PATH | URL | -
```

### Opciones

| Nombre, shorthand | Default   | Descripción  |
| ------------- |:--------------| ------------ |
| --tag , -t    |  | Nombre y opcionalmente una etiqueta en el formato 'nombre: etiqueta' |
| --build-arg   |  | Establecer variables de tiempo de construcción |

### Ejemplos
```bash
docker build .
docker build -t goals:latest .
docker build -t feedback-node:dev --build-arg DEFAULT_PORT=8000
```
<br>



## docker run

### Descripción

Docker ejecuta procesos en contenedores aislados. Un contenedor es un proceso que se ejecuta en un host. El anfitrión puede ser local o remoto. Cuando un operador ejecuta la ventana acoplable, el proceso contenedor que se ejecuta está aislado en el sentido de que tiene su propio sistema de archivos, su propia red y su propio árbol de procesos aislado separado del host.

### Uso

```bash
docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
```

### Opciones

| Nombre, shorthand | Default   | Descripción  |
| ------------- |:--------------| ------------ |
| -p    |  | Específica puertos a exponer de los contenedores (container:host) |
| -i    |  | Corre un contanedor de forma interactiva. |
| -t    |  | Correr contendor con una sesión TTY.
| -d    |  | Core un contenedor en modo detachable (desmontable)|
| --rm  |  | Al terminar de correr un contedor, este es eliminado del sistema de archivos. |
| -v    |  | Al crear un contenedor se crea un volumen para la persistencia de datos. |
| --name | | Al correr un contendor a este se le asigna un nombre. |
| --network | | Al correr un contenedor este es agregado a un red respectiva.

### Ejemplos
```bash
docker run -p 3000:3000 node
docker run -p 3000:3000 -d node
docker run -it node
docker run -p 3000:80 -d --rm node
docker run -p 3000:80 -d --rm --name goalsapp goals:latest
docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback feedback-node:volumes
docker run -d --name mongodb --network favorites-net mongo
docker run --name favorites --network favorites-net -d --rm -p 3000:3000 favorites-node
```
<br>



## docker container attach

### Descripción

Adjunte flujos de entrada, salida y error estándar locales a un contenedor en ejecución

### Uso

```bash
docker container attach [OPTIONS] CONTAINER
```

### Ejemplos
```bash
docker container attach node
```
<br>



## docker logs

### Descripción

Trae los registros de un contenedor

### Uso

```bash
docker logs [OPTIONS] CONTAINER
```

### Opciones

| Nombre, shorthand | Default   | Descripción  |
| ------------- |:--------------| ------------ |
| --follow , -f    |  | Sigue la salida del registro |

### Ejemplos
```bash
docker logs -f node
```
<br>



## docker ps

### Descripción

Lista los contenedores

### Uso

```bash
docker ps [OPTIONS]
```

### Opciones

| Nombre, shorthand | Default   | Descripción  |
| ------------- |:--------------| ------------ |
| --all , -a    |  | Muestra todos los contenedores |

### Ejemplos
```bash
docker ps
docker ps -a
```
<br>



## docker start

### Descripción

Inicia uno o más contenedores parados

### Uso

```bash
docker start [OPTIONS] CONTAINER [CONTAINER...]
```

### Opciones

| Nombre, shorthand | Default   | Descripción  |
| ------------- |:--------------| ------------ |
| --attach , -a    |  | Adjuntar STDOUT / STDERR y señales de reenvío |
| --interactive , -i |  | Adjuntar contenedor a STDIN |

### Ejemplos
```bash
docker start node-app
docker start -a node-app
docker start -ai node-app
```
<br>



## docker stop

### Descripción

Detiene uno o más contenedores corriendo

### Uso

```bash
docker stop [OPTIONS] CONTAINER [CONTAINER...]
```

### Ejemplos
```bash
docker stop node-app
```
<br>




docker container prune -> Remueve todos los contenedores parados.
docker rm <container> -> Remueve el container especificado.
docker images -> Lista todas las imágenes.
docker rmi <image_id> -> Remueve una imagen.
docker image prune -> Remueve todas la imagenes no usadas. Si un container utiliza una imagen, esta no es removida.
docker image prune -a -> Remueve todas la imagenes no usadas, así como las taggeadas. Si un container utiliza una imagen, esta no es removida.
docker image inspect <image_id> -> Inspeciona una imagen.
docker cp dummny/. <container>:/test -> Copia un archivo dentro de un container.
docker cp <container>:/test dummny -> Copia un archivo del container a nuestro local.
docker tag node-demo:latest academind/node-hello-world -> Renombra una imagen.
docker push memowii/node-hello-world:tagname -> Manda una imagen a docker hub.
docker login
docker logout
docker pull <image> -> Trae una imagen. La más nueva.
docker volume ls -> Lista todos lo volumenes.
docker volume rm VOL_NAME -> Remueve un volume.
docker volume prune -> Remueve todos los volumes.
docker volume create feedback-files -> Crea un volumen.
docker volume inspect
docker volume rm
docker container inspect <container>
docker network create favorites-net -> Crea un network.
docker network create --driver bridge my-net
docker exec -it <container> npm init

docker-compose up -> Start containers.
docker-compose up -d
docker-compose down -> Deletes containers and network.
docker-compose down -v -> Deletes containers, network and volumes.
docker-compose build -> Solo construye los containers.