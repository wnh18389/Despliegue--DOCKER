---
title: Ejercicio 4 - Redes
author: Víctor Benavides Alonso-Villaverde
---

# Ejercicio 4 - Redes

> Realizado por:  Víctor Benavides Alonso-Villaverde

[TOC]

## Despliegue de contenedores en red: Adminer y MariaDB



1. Acceder a `Adminer` desde un navegador con la url `http://localhost:8080`.

​	![image-20220201204927112](https://user-images.githubusercontent.com/83083348/152125670-59c33ce7-b7ae-4d09-96d0-3bdcc0bc6e04.png)



2. Crear una base de datos desde la Interfaz gráfica de `Adminer`.

![image-20220201205106414](https://user-images.githubusercontent.com/83083348/152125729-949bb03d-1c87-47e5-9675-d220325fdd2c.png)



![image-20220201205802090](https://user-images.githubusercontent.com/83083348/152125778-8e960f86-4f72-4391-81c7-88368e1dae92.png)

![image-20220201205921000](https://user-images.githubusercontent.com/83083348/152125825-c2d29997-d262-4820-beed-3cbbd7cd3309.png)


![image-20220201205941049](https://user-images.githubusercontent.com/83083348/152125886-7f55aec1-b934-4a79-8693-9ef832f57bb5.png)



3. Contenedores creados en ejecución.

   ```bash
   docker ps
   ```

![image-20220201210040501](https://user-images.githubusercontent.com/83083348/152125901-5eba684e-0bc8-40bb-8757-658337c26490.png)




4. Desde la terminal del servidor `MariaDB`, mostrar las bases de datos existentes, incluyendo la creada anteriormente.

   ```mariadb
   SHOW DATABASES
   ```

   

![image-20220201210629854](https://user-images.githubusercontent.com/83083348/152125919-3e20df2d-b9b1-4406-9fdd-a7a3b4350018.png)



5. Borrar los contenedores la red y los volúmenes utilizados.

   
![image](https://user-images.githubusercontent.com/83083348/152183430-04e7f900-a720-4924-bc4a-95f8ca28f181.png)
![image](https://user-images.githubusercontent.com/83083348/152183603-0f0c37b7-7d0e-43de-bccf-cfe7f447a431.png)
![image](https://user-images.githubusercontent.com/83083348/152184707-a02c8acb-2da4-49bf-862e-5225d74562f7.png)

