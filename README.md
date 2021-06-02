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