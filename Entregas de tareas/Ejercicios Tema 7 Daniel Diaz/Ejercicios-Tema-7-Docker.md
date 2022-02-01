---
title: Tema 7 - Docker
author: Daniel Díaz González
---

# Tema 5: Docker

> Daniel Díaz González - 2022

[TOC]



## 1 - Ejercicio inicial

Arranco docker

```bash
sudo docker
```

Creo el primer daemon a partir de la imagen nginx:

```bash
sudo docker run --name servidor_web -d -p 8181:80 nginx
```

![image-20220117093013115](Ejercicios-Tema-7-Docker.assets/image-20220117093013115.png)

![image-20220117093556137](Ejercicios-Tema-7-Docker.assets/image-20220117093556137.png)

Desde otra terminal compruebo que está correcto (Status Up)

![image-20220117094225888](Ejercicios-Tema-7-Docker.assets/image-20220117094225888.png)

Compruebo que se está ejecutando correctamente mediante un acceso a `localhost:8181` desde el navegador

<img src="Ejercicios-Tema-7-Docker.assets/image-20220117093922673.png" alt="image-20220117093922673" style="zoom:80%;" />

Y se registra el acceso:

![image-20220117094013298](Ejercicios-Tema-7-Docker.assets/image-20220117094013298.png)

Paro el contenedor `servidor_web` y compruebo desde otra terminal que se ha detenido correctamente

```bash
sudo docker stop servidor_web
```

![image-20220117095106907](Ejercicios-Tema-7-Docker.assets/image-20220117095106907.png)

Ahora elimino el contenedor `servidor_web` y compruebo que ya no queda rastro de él

```bash
sudo docker rm servidor_web
```

![image-20220117095246337](Ejercicios-Tema-7-Docker.assets/image-20220117095246337.png)



## 2 - Trabajo con imágenes y Servidor de base de datos

### 2.1 - Trabajo con imágenes

Arranco un contenedor de la imagen `php:7.4-apache` llamado `web` accesible a través del puerto 8000:

```bash
sudo docker run --name web -d -p 8000:80 php:7.4-apache
```

![image-20220117100035672](Ejercicios-Tema-7-Docker.assets/image-20220117100035672.png)

Coloco un fichero `index.html` y `mes.php` en en directorio `Documentos` de la máquina virtual y lo vinculo al directorio raíz del servicio web (`/var/www/html`) del contenedor:

```bash
sudo docker run -d -v /home/dani/Documentos:/var/www/html -p 8000:80 --name web php:7.4-apache
```

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121092631032.png" alt="image-20220121092631032" style="zoom:80%;" />

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121101847094.png" alt="image-20220121101847094" style="zoom:80%;" />

![image-20220121102143473](Ejercicios-Tema-7-Docker.assets/image-20220121102143473.png)

![image-20220121102049636](Ejercicios-Tema-7-Docker.assets/image-20220121102049636.png)



Compruebo el tamaño del contenedor `web`

```bash
sudo docker system df
```

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121102736655.png" alt="image-20220121102736655" style="zoom:80%;" />

```bash
sudo docker image ls
```

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121102958927.png" alt="image-20220121102958927" style="zoom:80%;" />

```bash
sudo docker ps --size
```

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121103143718.png" alt="image-20220121103143718" style="zoom:80%;" />

### 2.2 - Servidor de base de datos

Creo una red llamada `nuevaRed` y añado el contenedor que instancia `mariadb` en el puerto 3306, creando una base de datos automáticamente al iniciar llamada `prueba`

```bash
sudo docker network nuevaRed
sudo docker run --detach --network nuevaRed --name bbdd --env MARIADB_USER=invitado --env MARIADB_PASSWORD=invitado --env MARIADB_ROOT_PASSWORD=root  mariadb:latest MARIADB_DATABASE=prueba --port 3306

```

![image-20220128092759392](Ejercicios-Tema-7-Docker.assets/image-20220128092759392.png)

![image-20220128092727739](Ejercicios-Tema-7-Docker.assets/image-20220128092727739.png)

![image-20220128091718404](Ejercicios-Tema-7-Docker.assets/image-20220128091718404.png)




## 3 - Carga de ficheros a GitHub

### 3.1 - Prueba inicial

Creo una carpeta en local e inicio en ella un nuevo repositorio con un fichero de prueba (`prueba.html`)

![image-20220120105947188](Ejercicios-Tema-7-Docker.assets/image-20220120105947188.png)

```bash
git init
```

Tras editar el fichero de prueba, hago un `push` al repositorio creado por mi compañero

```bash
git add .
git status
git commit -m "Primer commit de prueba"
git remote add origin master https://github.com/wnh18389/Despliegue--DOCKER
git remote -v
git push origin master
```

![image-20220120110239195](Ejercicios-Tema-7-Docker.assets/image-20220120110239195.png)



### 3.2- Carga de documentos de la práctica

Añado a mi carpeta de trabajo los documentos que contienen la asignación de tareas y el Typora con los ejercicio inicial y de imágenes y servidor con base de datos:

```bash
git add .
git status
```

![image-20220128094953514](Ejercicios-Tema-7-Docker.assets/image-20220128094953514.png)

Hago el `commit` con todo lo nuevo en mi carpeta de trabajo:

```bash
git commit "Segundo commit con ejercicio 1 y 2 junto con asignacion de tareas"
```

![image-20220128095242400](Ejercicios-Tema-7-Docker.assets/image-20220128095242400.png)



Cargo todos los documentos al Github remoto de mi compañero:

```bash
git remote add origin master https://github.com/wnh18389/Despliegue--DOCKER
git remote -v
git push origin master
```

![image-20220128100028912](Ejercicios-Tema-7-Docker.assets/image-20220128100028912.png)



Comprobación de que todos los archivos cargaron correctamente:

![image-20220128100109323](Ejercicios-Tema-7-Docker.assets/image-20220128100109323.png)



## 4 - Links al hub del grupo y a la infografía utilizada:

**[Github del grupo de clase](https://github.com/wnh18389/Despliegue--DOCKER)**

[Uso de Git pull](https://www.atlassian.com/es/git/tutorials/syncing/git-pull)

[Dockerhub](https://hub.docker.com/_/mariadb)

[Pull request](https://aprendegit.com/que-es-un-pull-request/)



