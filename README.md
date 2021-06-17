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

Este comando creará el archivo de configuración mkdocs.yml y el archivo markdown index.md dentro del directorio docs, dentro de este directorio es donde publicaremos nuestros posts en markdown.

## Archivo de configuracion

Dentro del directorio del proyecto esta el archivo `mkdocs.yml` en donde indicamos brevemente la configuracion de la pagina y donde asignamos nuestros posts.
Debemos de configurarlo de la siguiente forma:

```
site_name: IAW

nav:
    - Principal: index.md
    - Acerca de: about.md

theme: material
```
Done `site_name` es el nombre de nuestra pagina, `theme` es el theme que usara nuestra pagina, y `nav` crea una pequeña sidebar en la pagina con titulos que enlaza a los archivos en markdown que tenemos el directorio `docs`.

## Lanzamiento del sitio
Para poner en marcha el sitio vamos a usar el comando `serve` desde el directorio `proyectos`, el cual nos permitira conectar a nuestra pagina de html con "nuestra ip":8000 

> docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material

El sitio deberia de verse asi:

![alt text](https://github.com/antoniomanu/antoniomanu.github.io/blob/main/capturas/mkdocs.png?raw=true)

## Github Pages
Despues de comprobar que funciona vamos a lanzarlo en nuestro repositorio de github de la siguiente forma:

1. Hacer que nuestro directorio proyecto sea un repositorio local.
> git init
2. Enlazar nuestro repositorio local con el repositorio que corresponde a MkDocs en Github.
> git remote add origin url_del_directorio
3. Lanzar el contenedor que nos subirá los archivos a Github. El cual nos pedirá los credenciales de usuario.
> docker run --rm -it -v ~/.ssh:/root/.ssh -v "$PWD":/docs squidfunk/mkdocs-material gh-deploy

Despues de esto deberiamos tener un branch nuevo en el repositorio que hemos creado donde se encuentren los archivos de MkDocs.
