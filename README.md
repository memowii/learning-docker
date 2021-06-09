# Learning Docker

Como meta de crecimiento personal, me propuse aprender docker con un enfoque más detallado y práctico. La razón de esto es porque docker siempre ha sido una tecnología que me ha costado discernir y asimilar.

Las notas, ejemplos y recetas encontradas en este proyecto fueron, en parte, tomadas de este curso [Docker & Kubernetes: The Practical Guide](https://www.udemy.com/course/docker-kubernetes-the-practical-guide/).

## Descripción de Docker

Docker es una plataforma abierta para desarrollar, enviar y ejecutar aplicaciones. Docker permite separar las aplicaciones de su infraestructura para que se pueda entregar software rápidamente. Con Docker, se puede administrar infraestructura de la misma manera que administra aplicaciones. Al aprovechar las metodologías de Docker para enviar, probar e implementar código rápidamente, se puede reducir significativamente la demora entre la escritura del código y su ejecución en producción.

## La plataforma Docker

Docker ofrece la capacidad de empaquetar y ejecutar una aplicación en un entorno aislado llamado contenedor. El aislamiento y la seguridad permiten ejecutar muchos contenedores simultáneamente en un host determinado. Los contenedores son livianos y contienen todo lo necesario para ejecutar la aplicación, por lo que no hay que depender de lo que está instalado actualmente en el host. En cuestiones laborales, se pueden compartir contenedores fácilmente, y asegurarse de que todas las personas con las que se comparte obtegan el mismo contenedor que funciona de la misma manera.

Docker proporciona herramientas y una plataforma para administrar el ciclo de vida de los contenedores:

* Desarrolle aplicaciones y sus componentes de soporte utilizando contenedores.
* El contenedor se convierte en una unidad para distribuir y probar aplicaciones.
* Implemente aplicaciones en su entorno de producción, como un contenedor o un servicio orquestado. Esto funciona igual si su entorno de producción es un centro de datos local, un proveedor de nube o un híbrido de los dos.

## ¿Para qué se puede usar Docker?

### Entrega rápida y consistente de aplicaciones

Docker agiliza el ciclo de vida del desarrollo al permitir que los desarrolladores trabajen en entornos estandarizados utilizando contenedores locales que proveen a las aplicaciones y servicios. Los contenedores son ideales para la integración continua y los flujos de trabajo de entrega continua (CI / CD).

### Implementación y escalado receptivos

La plataforma basada en contenedores de Docker permite cargas de trabajo altamente portátiles. Los contenedores Docker pueden ejecutarse en una computadora portátil de un desarrollador, en máquinas físicas o virtuales en un centro de datos, en proveedores de la nube o en una combinación de entornos.

### Ejecutar más cargas de trabajo en el mismo hardware

Docker es ligero y rápido. Proporciona una alternativa viable y rentable a las máquinas virtuales basadas en hipervisores, por lo que puede utilizar una mayor parte de su capacidad informática para lograr sus objetivos comerciales. Docker es perfecto para entornos de alta densidad y para implementaciones pequeñas y medianas donde necesita hacer más con menos recursos.

## Arquitectura de Docker

Docker utiliza una arquitectura cliente-servidor. El cliente de Docker habla con el demonio de Docker, que hace el trabajo pesado de compilar, ejecutar y distribuir los contenedores. El cliente y el demonio pueden ejecutarse en el mismo sistema, o  puede conectarse un cliente de Docker a un demonio de Docker remoto. El cliente y el demonio se comunican mediante una API REST, a través de sockets UNIX o una interfaz de red. Otro cliente de Docker es Docker Compose, que le permite trabajar con aplicaciones que constan de un conjunto de contenedores.

![arquitectura de Docker](https://docs.docker.com/engine/images/architecture.svg)

### El demonio de Docker🔗

El demonio de Docker (dockerd) escucha las solicitudes de la API de Docker y administra los objetos de Docker, como imágenes, contenedores, redes y volúmenes. Un demonio también puede comunicarse con otros demonios para administrar los servicios de Docker.

### El cliente Docker

El cliente de Docker (Docker) es la forma principal en que muchos usuarios de Docker interactúan con Docker. Cuando se usan comandos como docker run, el cliente envía estos comandos a dockerd, que los ejecuta. El comando de Docker usa la API de Docker. El cliente de Docker puede comunicarse con más de un demonio.

### Registros de Docker

Un registro de Docker almacena imágenes de Docker. Docker Hub es un registro público que cualquiera puede usar y Docker está configurado para buscar imágenes en Docker Hub de forma predeterminada. Incluso puede ejecutar su propio registro privado.

Cuando usa los comandos `docker pull` o `docker run`, las imágenes requeridas se extraen de su registro configurado. Cuando usa el comando `docker push`, su imagen se envía a su registro configurado.

### Objetos Docker🔗

Cuando usa Docker, está creando y usando imágenes, contenedores, redes, volúmenes, complementos y otros objetos. Esta sección es una breve descripción general de algunos de esos objetos.

### Imágenes

Una imagen es una plantilla de solo lectura con instrucciones para crear un contenedor Docker. A menudo, una imagen se basa en otra imagen, con alguna personalización adicional. Por ejemplo, puede crear una imagen basada en la imagen de ubuntu, pero instala el servidor web Apache y su aplicación, así como los detalles de configuración necesarios para ejecutar su aplicación.

Puede crear sus propias imágenes o puede usar solo las creadas por otros y publicadas en un registro. Para crear su propia imagen, cree un Dockerfile con una sintaxis simple para definir los pasos necesarios para crear la imagen y ejecutarla. Cada instrucción en un Dockerfile crea una capa en la imagen. Cuando cambia el Dockerfile y reconstruye la imagen, solo se reconstruyen las capas que han cambiado. Esto es parte de lo que hace que las imágenes sean tan ligeras, pequeñas y rápidas en comparación con otras tecnologías de virtualización.

### Contenedores

Un contenedor es una instancia ejecutable de una imagen. Puede crear, iniciar, detener, mover o eliminar un contenedor mediante la API de Docker o la CLI. Puede conectar un contenedor a una o más redes, adjuntarle almacenamiento o incluso crear una nueva imagen basada en su estado actual.

De forma predeterminada, un contenedor está relativamente bien aislado de otros contenedores y de su máquina host. Puede controlar qué tan aislados están la red, el almacenamiento u otros subsistemas subyacentes de un contenedor de otros contenedores o de la máquina host.

Un contenedor se define por su imagen, así como por las opciones de configuración que le proporcione al crearlo o iniciarlo. Cuando se quita un contenedor, cualquier cambio en su estado que no esté almacenado en el almacenamiento persistente desaparece.

### Ejemplo de comando `docker run`

El siguiente comando ejecuta un contenedor `ubuntu`, se adjunta de forma interactiva a su sesión de línea de comandos local y ejecuta `/bin/bash`.

```bash
$ docker run -i -t ubuntu /bin/bash
```

1. Si no tiene la imagen de `ubuntu` localmente, Docker la extrae de su registro configurado, como si hubiera ejecutado `docker pull ubuntu` manualmente.
2. Docker crea un nuevo contenedor, como si hubiera ejecutado manualmente un comando de creación de contenedor de Docker.
3. Docker asigna un sistema de archivos de lectura y escritura al contenedor, como su capa final. Esto permite que un contenedor en ejecución cree o modifique archivos y directorios en su sistema de archivos local.
4. Docker crea una interfaz de red para conectar el contenedor a la red predeterminada, ya que no especificó ninguna opción de red. Esto incluye la asignación de una dirección IP al contenedor. De forma predeterminada, los contenedores pueden conectarse a redes externas mediante la conexión de red de la máquina host.
5. Docker inicia el contenedor y ejecuta `/bin/bash`. Debido a que el contenedor se ejecuta de forma interactiva y está adjunto a su terminal (debido a los indicadores `-i` y `-t`), puede proporcionar entrada usando su teclado mientras la salida se registra en su terminal.
6. Cuando escribe `exit` para terminar el comando `/bin/bash`, el contenedor se detiene pero no se elimina. Puede iniciarlo de nuevo o eliminarlo.

### La tecnología subyacente

Docker está escrito en el lenguaje de programación Go y aprovecha varias características del kernel de Linux para ofrecer su funcionalidad. Docker usa una tecnología llamada `namespaces` para proporcionar el espacio de trabajo aislado llamado contenedor. Cuando ejecuta un contenedor, Docker crea un conjunto de namespaces para ese contenedor.

Estos namespaces proporcionan una capa de aislamiento. Cada aspecto de un contenedor se ejecuta en un namespace separado y su acceso está limitado a ese namespace.