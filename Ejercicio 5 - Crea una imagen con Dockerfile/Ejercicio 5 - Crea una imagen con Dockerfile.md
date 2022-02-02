---
title: Ejercicio 5 - Crea una imagen con Dockerfile
author: Martin Laviada Brun
---

# Ejercicio 5 - Crea una imagen con Dockerfile

> Realizado por: MartinLB

[TOC]

## Crear una imagen con un servidor web que sirva un sitio web

1. Basar la imagen en `nginx` o `apache`.

   ```dockerfile
   FROM nginx:latest
   ADD proyecto-git-remoto/ /usr/share/nginx/html
   EXPOSE 80
   ```

   ![image-20220131182300083](Ejercicios-Tema-7-Docker.assets/image-20220131182300083.png)

   

2. Desplegar una plantilla, o un trabajo de clase, que tenga, al menos, un `index.html` y una carpeta para estilos, imágenes, etc.

   ```bash
   docker build -t martinlb18/dockerfiletarea:v1 .
   ```

   ![image-20220131182330487](Ejercicios-Tema-7-Docker.assets/image-20220131182330487.png)



3. Subir la imagen a DockerHub.

   ```bash
   docker login
   ```

   ![login Docker](Ejercicios-Tema-7-Docker.assets/loginDocker.PNG)

   

   ```bash
   docker push martinlb18/dockerfiletarea:v1
   ```

   ![image-20220131182851441](Ejercicios-Tema-7-Docker.assets/image-20220131182851441.png)

   

   ![image-20220131182942382](Ejercicios-Tema-7-Docker.assets/image-20220131182942382.png)



4. Bajada de la imagen por otra persona del grupo.

![image-20220202114513158](Ejercicios-Tema-7-Docker.assets/image-20220202114513158.png)



```bash
docker pull martinlb18/dockerfiletarea
```

![image-20220202165416180](Ejercicios-Tema-7-Docker.assets/image-20220202165416180.png)



5. Creación de contenedor y acceso al navegador del sitio.

   ```bash
   sudo docker run -d -p 80:80 martinlb18/dockerfiletarea:v1
   ```

![image-20220202165718942](Ejercicios-Tema-7-Docker.assets/image-20220202165718942.png)



![image-20220202165800527](Ejercicios-Tema-7-Docker.assets/image-20220202165800527-16438400310131.png)
