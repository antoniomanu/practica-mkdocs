# Creación de un sitio web estático con MkDocs

## Introduccion
MkDocs es un generador de sitios web estáticos que nos permite crear de forma sencilla un sitio web para documentar un proyecto. El contenido del sitio web está escrito en texto plano en formato Markdown y se configura con un único archivo de configuración en formato YAML.

## Primeros pasos
Para poder hacer esta practica podemos usar cualquier maquina de ubuntu, simplemente tendremos que abrir el puerto 22 para conectar por SSH y el puerto 8000.

Una vez dentro de la consola instalaremos docker y docker-compose, para asi poder descargar el contenedor de MkDocs desde docker, en este caso descargaremos uno con el theme Material.

> docker pull squidfunk/mkdocs-material

## Creacion del Proyecto
Primero crearemos un directorio con el nombre que queramos, en este caso se llamara `proyecto`; y nos movemos a este, desde ese directorio usaremos el comando `new` para crear los archivos del directorio

> docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material new .

Este comando creará el archivo de configuración mkdocs.yml y el archivo Markdown index.md dentro del directorio docs, dentro de este directorio es donde publicaremos nuestros posts en markdown.

## Archivo de configuracion

Dentro del directorio del proyecto esta el archivo `mkdocs.yml` en donde indicamos brevemente la configuracion de la pagina y donde asignamos nuestros posts.
Debemos de configurarlo de la siguiente forma:

```site_name: IAW

nav:
    - Principal: index.md
    - Acerca de: about.md

theme: material```
