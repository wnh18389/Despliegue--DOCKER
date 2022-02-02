---
title: Ejercicio 2 - Trabajo con imágenes
author: Daniel Díaz González
---

# Ejercicio 2 - Trabajo con imágenes

> Daniel Díaz González - 2022

[TOC]

## 1 - Servidor Web

1. Arranco un contenedor de la imagen `php:7.4-apache` llamado `web` accesible a través del puerto 8000.

```bash
sudo docker run --name web -d -p 8000:80 php:7.4-apache
```

![image-20220117100035672](Ejercicios-Tema-7-Docker.assets/image-20220117100035672.png)



2. Coloco un fichero `index.html` y `mes.php` en en directorio `Documentos` de la máquina virtual y lo vinculo al directorio raíz del servicio web (`/var/www/html`) del contenedor.

```bash
sudo docker run -d -v /home/dani/Documentos:/var/www/html -p 8000:80 --name web php:7.4-apache
```

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121092631032.png" alt="image-20220121092631032" style="zoom:80%;" />

<img src="Ejercicios-Tema-7-Docker.assets/image-20220121101847094.png" alt="image-20220121101847094" style="zoom:80%;" />

![image-20220121102143473](Ejercicios-Tema-7-Docker.assets/image-20220121102143473.png)

![image-20220121102049636](Ejercicios-Tema-7-Docker.assets/image-20220121102049636.png)



3. Compruebo el tamaño del contenedor `web`.

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






## 2 - Servidor de base de datos

1. Creo una red llamada nuevaRed y añado el contenedor que instancia mariadb en el puerto 3306, creando una base de datos automáticamente al iniciar llamada prueba.

```bash
sudo docker network nuevaRed
sudo docker run --detach --name bbdd --env MARIADB_USER=invitado
--env MARIADB_PASSWORD=invitado --env MARIADB_ROOT_PASSWORD=root MARIADB_DATABASE=prueba --port 3336:3306 mariadb:latest
```

![image-20220128092759392](Ejercicios-Tema-7-Docker.assets/image-20220128092759392.png)

![image-20220128092727739](Ejercicios-Tema-7-Docker.assets/image-20220128092727739.png)

![image-20220128091718404](Ejercicios-Tema-7-Docker.assets/image-20220128091718404.png)


2. Hago una instancia de un cliente de base de datos (phpMyAdmin) y conecto para comprobar el acceso al servidor de base de datos con el usuario creado (invitado) y que se ha creado la base de datos `prueba`.

```bash
sudo docker run --name myadmin -d -e PMA_ARBITRARY=1 --link bbdd:mariadb -p 8080:80 phpmyadmin
```

![MicrosoftTeams-image](https://user-images.githubusercontent.com/83083348/152231115-ef85a753-c11a-4e3f-9244-6f50ce454e82.png)
![MicrosoftTeams-image (1)](https://user-images.githubusercontent.com/83083348/152231358-bdbc7c4c-47a9-4087-89e6-93e9af6f0e82.png)
![MicrosoftTeams-image (2)](https://user-images.githubusercontent.com/83083348/152231411-f60ade8d-0325-4210-bf5c-f58eba9e2dc2.png)

Pantallazo donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado.

```bash
sudo docker images -a
sudo docker rmi mariadb
sudo docker images -a
```

![MicrosoftTeams-image (3)](https://user-images.githubusercontent.com/83083348/152231616-567bc5ca-0e7d-472c-8e3d-c76f86020dda.png)

