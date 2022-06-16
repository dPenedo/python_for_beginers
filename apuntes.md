#DJANGO FOR BEGINERS

## Capítulo 1
* Instalacion de Python, de pyenv, django, git y recomendaciones sobre elegir un editor de código.
* Generar un entorno, empezando un proyecto y llamar a la carpeta 'Django'


## Capítulo 2
* Generar un entorno y llamar a la carpeta 'Helloworld'
* Iniciar un proyecto y surge el siguiente árbol sobre el proyecto helloworld:
    - Pipfile
    - Pipfile.locl
    - helloworld_project
	- __init__.py
	- settings.py 	(Controla la configuración)
	- urls.py 	(Gestiona las URLs que se construyen en el navegador)
	- wsgi.py 	(Es la Web Server Gateway Interface. Describe cómo se comunica un servidor web con una aplicación web, y cómo se pueden llegar a encadenar diferentes aplicaciones web para procesar una solicitud/petición (o request))
    - manage.py 	(Ejecuta comandos de django)

Django usa dos conceptos para ordenar el contenido:
- Proyecto: contiene una o más aplicaciones que relacionadas suponen una aplicación web. Se inicializa con el comando'startproject'
- Aplicaciones: Cada una de las funcionalidades que forman parte del proyecto. Se inicializa con el comando 'startapp'.

* Se inicia una app llamada 'pages' y el árbol queda así:

- Pages
    - __init__.py
    - admin.py 		(archivo de configuración para el Django Admin)
    - apps.py 		(archivo de configuración para la aplicación)
    - migrations 	(sincroniza los cambios de models.py)
	- __init__.py
    - models.py 	(se definen los modelos de bases de datos, que Django traducirá a tablas de bases de datos)
    - tests.py 		(Para los tests específicos de la app)
    - views.py 		(Se manejan las peticiones y respuestas de la app)

* Se añade la app 'pages' a settings.py

Cuando se hace una petición HTTP se sigue el siguiente modelo:

URL -> View -> Modelo (normalmente) -> Plantilla

* En Pages se edita el archivo views.py
* En Pages se edita el archivo urls.py
* En el proyecto se edita el archivo urls.py (es un archivo diferente al anterior)


