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



## docker container prune

### Descripción

Retira todos los contenedores detenidos

### Uso

```bash
 docker container prune [OPTIONS]
```
### Ejemplos
```bash
docker container prune
```
<br>



## docker rm

### Descripción

Retira uno o más contenedores

### Uso

```bash
 docker rm [OPTIONS] CONTAINER [CONTAINER...]
```

### Ejemplos
```bash
docker rm node
```
<br>



## docker images

### Descripción

Lista de imágenes

### Uso

```bash
docker images [OPTIONS] [REPOSITORY[:TAG]]
```

### Ejemplos
```bash
docker images
```
<br>



## docker rmi

### Descripción

Eliminar una o más imágenes

### Uso

```bash
docker rmi [OPTIONS] IMAGE [IMAGE...]
```

### Ejemplos
```bash
docker rmi node-image
```
<br>



## docker image prune

### Descripción

Elimina imágenes no utilizadas

### Uso

```bash
docker image prune [OPTIONS]
```

### Ejemplos
```bash
docker image prune
```
<br>



## docker image inspect

### Descripción

Muestra información detallada sobre una o más imágenes.

### Uso

```bash
docker image inspect [OPTIONS] IMAGE [IMAGE...]
```

### Ejemplos
```bash
docker image inspect node
```
<br>



## docker cp

### Descripción

Copie archivos / carpetas entre un contenedor y el sistema de archivos local

### Uso

```bash
docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-
```

### Ejemplos
```bash
docker cp dummny/. node:/test
docker cp node:/test dummny
```
<br>



## docker tag

### Descripción

Cree una etiqueta TARGET_IMAGE que haga referencia a SOURCE_IMAGE

### Uso

```bash
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```

### Ejemplos
```bash
docker tag node-demo:latest academind/node-hello-world
```
<br>



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
```
<br>