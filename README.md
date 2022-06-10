# ExamenSistemas | Adrià Juan de León

![image](https://user-images.githubusercontent.com/98842240/173083398-6debe84f-629a-4931-98bc-fe580a837c9c.png)

___
- Introducción.
___
- ¿Que es Docker?

Docker es un proyecto de código abierto que automatiza el despliegue de aplicaciones dentro de contenedores de software, proporcionando una capa adicional de abstracción y automatización de virtualización de aplicaciones en múltiples sistemas operativos.

- ¿Que es Docker-Compose?

Docker Compose es una herramienta para definir y ejecutar aplicaciones de Docker de varios contenedores. En Compose, se usa un archivo YAML para configurar los servicios de la aplicación. Después, con un solo comando, se crean y se inician todos los servicios de la configuración.

- ¿Que es DockerFile?

Un DockerFile es un documento de texto que contiene todos los comandos que queramos ejecutar en la linea de comandos para armar una imágen. Esta imágen se creará mediante el comando docker build que irá siguiendo las instrucciones.

___
- Primer Paso.
___

El primer paso a realizar es bajarnos el **.war**, en este caso hemos descargado el proyecto del profesor Máximo ya que el nuestro daba errores.

- NOTA: Para ello hemos ido al repositorio del profesor y nos hemos descagado su **.war**.

___
- Segundo paso.
___

El segundo paso es la creación de la carpeta y archivos de **Dcokerfile** y **docker-compose.yml**.

A continuación hemos creado una carpeta con el nombre del proyecto, en este caso la carpeta se llama: **DockerCompose**.

![image](https://user-images.githubusercontent.com/98842240/173104783-00bc7b9a-18c0-48af-b92d-3bf71df3f53e.png)

Dentro de esta carpeta hemos metido la siguiente estructura de archivos:

![image](https://user-images.githubusercontent.com/98842240/173105023-840891a7-fe47-4e54-8109-d75c88824c75.png)

Cuando tengamos todo listo, debemos crear un archivo llamado **Dockerfile** (esto debe estar creado dentro VisualEstudio ya que me deja abrir la carpeta entera).

![image](https://user-images.githubusercontent.com/98842240/173105331-fa6e4774-d8af-4b18-9eb9-b2fa7d7c0b8d.png)

Después de haber creado el **Dockerfile**, debemos añadir la siguiente información dentro del archivo:

``
FROM tomcat:latest

LABEL maintainer="Adria Juan de Leon"

COPY ./target/LoginWebApp.war /usr/local/tomcat/webapps/

EXPOSE 8080

CMD ["catalina.sh", "run"]
``
