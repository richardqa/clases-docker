<figure>
<img src="http://opennetsoft.com/images/IMAGENES/docker1/Logo2-oficial.png" alt="" />
</figure>

Ejemplo1: Construyendo un contenedor con Tomcat 
===============================================

Este es un ejemplo básico de *construir* una imagen de Tomcat usando *Dockerfile*, el cual copia un archivo *Java WAR* al directorio /webapps de Tomcat. Una vez construido la imagen, puedes hacer *PUSH* a tu repositorio personal de Docker Hub y luego ejecutar un contenedor usando esta imagen en cualquier plataforma (Linux o Windows) con Docker instalado.

### Clona tu proyecto

Para clonar tu proyecto:  
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
git clone https://github.com/richardqa/docker-examples
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Construir una imagen usando el proyecto clonado:

cd docker-examples/

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker build -t richardqa/mitomcat:v1 .
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Te autenticas con tu cuenta de Docker Hub y creas un repositorio de Tomcat público.

-   Registras una cuenta libre en Docker Hub – <a href="https://hub.docker.com/">***https://hub.docker.com/***</a>

-   Creas un repositorio público llamado Tomcat

### Push de la imagen creada a tu Docker Hub

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker login
docker push richardqa/mitomcat:v1
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Ejecutar un contenedor llamado Tomcat usando la imagen que construiste:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker run -p 8080:8080 -d --name tomcat  <your-username>/tomcat:latest
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Acceso a la aplicación ejemplo:

Puedes acceder a la aplicación ejemplo de Tomcat yendo a la siguiente URL:

http://<host-ip>:8080/sample

### Acceso a los *Logs*

Puedes usar un simple comando para revisar los logs de *Catalina* de tu contenedor Tomcat

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker logs tomcat
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### Revisar los archivos dentro de tu contenedor Tomcat

Puedes ejecutar el comando *docker exec* para entrar al contenedor y revisar los archivos bajo el directorio *webapps*

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
docker exec -it tomcat bash
ls -lrt /usr/local/tomcat/webapps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

