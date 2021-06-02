docker build . -> Ejecuta el archivo Dockerfile local. También puede reconstruir una imagen.
docker run -p 3000:3000 da7d1149e8a3 -> Crea y corre un contenedor con id da7d1149e8a3, y expone el puerto 3000.
docker run -p 3000:3000 -d da7d1149e8a3 -> Crea y corre un contenedor con id da7d1149e8a3, y expone el puerto 3000, en detached mode.
docker run -it 4c62b4a9f6ee -> Corre un contenedor en modo interactivo y con tty.
docker container attach <container> -> Attach to a running container.
docker logs -f <container> -> Muestra los logs del contenedor y te hace un attach.
docker ps -> Muestra contanedores que se están ejecutando actualmente.
docker stop <name> -> Stops a docker container.
docker run node -> Descarga la imagen node, y corre el container.
docker ps -a -> Muestra todos los contenedores.
docker run -it node -> Corre node con una sesión interactiva dentro del contenedor.
docker start <container> -> Starts a container.
docker start -a <container> -> Starts a container con attach mode.
docker start -ai <container> -> Inicia un container en attach e interactive mode. Sirve para aplicaciones de utilería.
docker container prune -> Remueve todos los contenedores parados.
docker rm <container> -> Remueve el container especificado.
docker images -> Lista todas las imágenes.
docker rmi <image_id> -> Remueve una imagen.
docker image prune -> Remueve todas la imagenes no usadas. Si un container utiliza una imagen, esta no es removida.
docker image prune -a -> Remueve todas la imagenes no usadas, así como las taggeadas. Si un container utiliza una imagen, esta no es removida.
docker run -p 3000:80 -d --rm <image> -> Corre un container y luego elimina ese container
docker image inspect <image_id> -> Inspeciona una imagen.
docker cp dummny/. <container>:/test -> Copia un archivo dentro de un container.
docker cp <container>:/test dummny -> Copia un archivo del container a nuestro local.
docker run -p 3000:80 -d --rm --name goalsapp <container> -> Corre un container con un nombre.
docker run -p 3000:80 -d --rm --name goalsapp goals:latest
docker build -t goals:latest . -> Crea una imagen con un tag.
docker tag node-demo:latest academind/node-hello-world -> Renombra una imagen.
docker push memowii/node-hello-world:tagname -> Manda una imagen a docker hub.
docker login
docker logout
docker pull <image> -> Trae una imagen. La más nueva.
docker volume ls -> Lista todos lo volumenes.
docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback feedback-node:volumes -> Inicia un container con un named volume.
docker volume rm VOL_NAME -> Remueve un volume.
docker volume prune -> Remueve todos los volumes.
docker volume create feedback-files -> Crea un volumen.
docker volume isnpect
docker volume rm

docker container isnpaect <container>
docker network create favorites-net -> Crea un network.
docker network create --driver bridge my-net
docker run -d --name mongodb --network favorites-net mongo -> Corre un mongo container attacheado a la network pasada.
docker run --name favorites --network favorites-net -d --rm -p 3000:3000 favorites-node

docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback -v "/home/memowii/Programming/courses/udemy/docker-&-kubernetes-the-practical-guide/section-3/data-volumes-01-starting-setup:/app" -v /app/node_modules feedback-node:volumes -> Crea un container con un bind mount.
docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback -v $(pwd):/app -v /app/node_modules feedback-node:volumes
docker run -d -p 3000:80 --rm --name feedback-app -v feedback:/app/feedback -v $(pwd):/app:ro -v /app/temp -v /app/node_modules feedback-node:volumes -> Iniciar un container con un volume read only. Docker no va a poder modificar los archivos del volume. 

docker run -d -p 3000:8000 --rm --env PORT=8000 --name feedback-app -v feedback:/app/feedback -v "/home/memowii/Programming/courses/udemy/docker-&-kubernetes-the-practical-guide/section-3/data-volumes-01-starting-setup:/app:ro" -v /app/node_modules -v /app/temp feedback-node:env -> Especifa variable de entorno.
docker run -d -p 3000:8000 --rm --env-file ./.env --name feedback-app -v feedback:/app/feedback -v "/home/memowii/Programming/courses/udemy/docker-&-kubernetes-the-practical-guide/section-3/data-volumes-01-starting-setup:/app:ro" -v /app/node_modules -v /app/temp feedback-node:env -> Especifa variable de entorno.

docker build -t feedback-node:dev --build-arg DEFAULT_PORT=8000

docker run -p 3000:80 d80f19be89cb

docker-compose up -> Start containers.
docker-compose up -d
docker-compose down -> Deletes containers and network.
docker-compose down -v -> Deletes containers, network and volumes.
docker-compose build -> Solo construye los containers.

docker run -it node -> Corre el container node en modo interactivo. 
docker run -it -d node
docker exec -it <container> npm init
docker run -it node npm init