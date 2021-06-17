# Creación de un sitio web estático con MkDocs

## Introduccion
MkDocs es un generador de sitios web estáticos que nos permite crear de forma sencilla un sitio web para documentar un proyecto. El contenido del sitio web está escrito en texto plano en formato Markdown y se configura con un único archivo de configuración en formato YAML.

## Primeros pasos
Para poder hacer esta practica podemos usar cualquier maquina de ubuntu, simplemente tendremos que abrir el puerto 22 para conectar por SSH y el puerto 8000.

Una vez dentro de la consola instalaremos docker y docker-compose, para asi poder descargar el contenedor de MkDocs desde docker, en este caso descargaremos uno con el theme Material.

> docker pull squidfunk/mkdocs-material

## Creacion del Proyecto
Primero crearemos un repositorio con el nombre que queramos, en este caso se llamara `proyecto`
