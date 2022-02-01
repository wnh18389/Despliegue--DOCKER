---
title: Ejercicio 1 - Inicial
author: Daniel Díaz González
---

# Ejercicio 1 - Inicial

> Daniel Díaz González - 2022

[TOC]

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