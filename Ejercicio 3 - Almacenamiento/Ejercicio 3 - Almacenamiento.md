---
title: Ejercicio 3 - Almacenamiento
author: Martin Laviada Brun
---

# Ejercicio 3 - Almacenamiento

> Realizado por: MartinLB

[TOC]

## Bind mount para compartir datos

1. Crea una carpeta llamada `saludo` y dentro de ella crea un fichero llamado `index.html` con el siguiente contenido:

   ```html
   <h1>HOLA SOY XXXXXX</h1>
   ```

   ```bash
   mkdir saludo
   cd saludo/
   echo "<h1>HOLA SOY MARTIN</h1>" > index.html
   ```

   ![image-20220131180607279](Ejercicios-Tema-7-Docker.assets/image-20220131180607279.png)



2. Una vez hecho esto arrancar dos contenedores basados en la imagen php:7.4- apache que hagan un bind mount de la carpeta `saludo` en la carpeta `/var/www/html` del contenedor. Uno de ellos vamos a acceder con el puerto 8181 y el otro con el 8282. Y su nombres serán `c1` y `c2` .

   ```bash
   docker run -d --name c1 -p 8181:80 -v ~/saludo:var/www/html php:7.4-apache
   ```

   ![image-20220131181017125](Ejercicios-Tema-7-Docker.assets/image-20220131181017125.png)

   ```bash
   docker run -d --name c2 -p 8282:80 -v ~/saludo:var/www/html php:7.4-apache
   ```

   ![image-20220131181053669](Ejercicios-Tema-7-Docker.assets/image-20220131181053669.png)

   ![lista c1 c2](Ejercicios-Tema-7-Docker.assets/listac1c2.PNG)

   

   **Resultado:**

   ![image-20220131181302673](Ejercicios-Tema-7-Docker.assets/image-20220131181302673.png)



3.  Modifica el contenido del fichero `~/saludo/index.html`.

   ```bash
   mv ~/proyecto-git-remoto/* ~/saludo
   ```

   ![image-20220131181415492](Ejercicios-Tema-7-Docker.assets/image-20220131181415492.png)



4. Comprueba que puedes seguir accediendo a los contenedores, sin necesidad de reiniciarlos.

   ![paginaCambiada](Ejercicios-Tema-7-Docker.assets/paginaCambiada-16436494563081.PNG)



5. Borra los contenedores utilizados.

   ![image-20220131181853752](Ejercicios-Tema-7-Docker.assets/image-20220131181853752.png)

   ![image-20220131181829426](Ejercicios-Tema-7-Docker.assets/image-20220131181829426.png)

![image-20220131181901712](Ejercicios-Tema-7-Docker.assets/image-20220131181901712.png)