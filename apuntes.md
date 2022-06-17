#DJANGO FOR BEGINERS

## Capítulo 1
* Instalacion de Python, de pyenv, django, git y recomendaciones sobre elegir un editor de código.
* Generar un entorno, empezando un proyecto y llamar a la carpeta 'Django'


## Capítulo 2
* Generar un entorno ('$ pipenv shell') y llamar a la carpeta 'Helloworld'
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
* En el proyecto se edita el archivo urls.py (es un archivo diferente al anterior). Se le añade el método django.urls.include() y así se le añade directamente la app de pages sin tener que importarla al nivel del proyecto.

Después explica como crear un git y subirlo a Bitbucket (una alternativa a GitHub), porque al parecer cuando se escribió el libro no se podían hacer repositorios privados en GitHub.


## Capítulo 3

En el capítulo creará una app llamada Pages que tiene su propia homepage y un página about.

* Crear carpeta pages, entorno pipenv, startproject y startapp

* Añadir la aplicación pages al archivo settings.py



#### Plantillas

Las plantillas (templates) generan archivos HTML.

Con Django constantemente se editan y crean estos tres elementos: 
- URLs: es donde se enruta dentro de la página.
- Views: contienen la lógica de qué sucede en ellos.
- Plantilla: contiene el HTML.

A nivel organizativo se puede generar una carpeta 'templates' con carpetas para cada app. Pero el enfoque que sigue en el libro es el de generar una única carpeta 'templates' a nivel de proyecto para todas las apps.

* Se crea una carpeta templates y dentro un archivo home.html
* Se edita el archivo settings.py para que contenga la carpeta creada dentro de la sección TEMPLATES y en 'DIRS.
* Se le añade un h1 al archivo html

Las views se realizan mediante clases. Al principio de Django, tenía un enfoque de funciones, pero se le añadió un enfoque basado en clases para evitar repetir código innecesario.

* Se añade el módulo TemplateView al archivo views y se le agrega la plantilla creada a la clase HomePageView
 
 Después se tienen que editar las URLs

* Se actualiza el urls.py a nivel de proyecto
* Se le añade un archivo urls.py a la carpeta pages (pages/pages) a nivel de app.
* Se escribe dentro del urls.py a nivel de app y al estar basado en clases se le añade add_view() al final del nombre.


De manera similar al archivo home.html se le suma una página about en un archivo about.html

* Se crea el archivo.html
* Se le añade un h1
* Se añade al pages/views.py
* Se añade al urls.py de la app

