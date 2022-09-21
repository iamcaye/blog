---
layout:     post
title:      Docker Cheatsheet
date:       2022-09-21
categories: research
---

## Comandos
* Listado de imagenes descargas
```bash
docker images
```
* Descargar una imagen
```bash
docker pull <imagen>:<version>
```
* Listado de imagenes disponibles: <a href='https://hub.docker.com/' target='_noopener'>Docker Hub</a>
* Crear un contenedor:
```bash
docker create --name <name> <imagen>
```
Devuele el id del contenedor creado
* Iniciar un contenedor
```bash
docker start <container>
```
* Parar un contenedor
```bash
docker stop <container>
```
* Listado de containers corriendo actualmente
```bash
docker ps
```
* Listado de containers creados
```bash
docker ps -a
```
* Eliminar un continer
```bash
docker rm <container>
```
* Port mapping
```bash
docker -p<puerto-local>:<puerto-docker> --name <name> <imagen>
```
* Mostrar logs del contenedor
```bash
docker logs --follow <container> 
```
* PULL + CREATE + START
```bash
docker run --name <name> -p<puerto>:<puerto-docker> -d <imagen>
```


## DockerFile
Se usa para especificar las acciones que realizara el container al iniciarse
* Ejemplo básico con node

```DockerFile
FROM node:18 // <imagen>:<version>

RUN mkdir -p /home/app // crea la carpeta dentro del docker donde vamos a alojar la app
COPY . /home/app // copiamos el proyecto dentro de la carpeta que hemos creado

EXPOSE 3000  // puerto que se va exponer dentro del container
CMD ["node", "/home/app/index.js"]
```
* Para hacer una build de una imagen
```bash
docker build -t <nombre>:<version>
```

# Conexion entre contenedores
* Para listar todas las redes
```bash
docker network ls
```
* Para crear una red nueva
```bash
docker network create <name>
```
* Para configurar conexiones entre imagenes dentro de un mismo contenedor la red existente se llama igual que el controlador
