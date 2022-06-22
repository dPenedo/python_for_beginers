# About 

Este un proyecto en desarollo de la lectura del libro Python for Beginers de William S. Vincent.
En este [github](https://github.com/wsvincent/djangoforbeginners) de su propia autoría están todos los proyectos hechos.

En este archivo README están los apuntes tomados durante la lectura y práctica del libro, todo en castellano. No trata de ser un resumen exhaustivo del libro, sino que son notas tomadas durante la lectura.

## Índice de contenidos

- Capítulo 1: [Set Up Inicial](#id-section1)
- Capítulo 2: [app Hello World](#id-section2)
- Capítulo 3: [app Pages](#id-section3)
- Capítulo 4: [](#id-section4)
- Capítulo 6: [](#id-section6)
- Capítulo 7: [](#id-section7)
- Capítulo 8: [](#id-section8)
- Capítulo 9: [](#id-section9)
- Capítulo 10: [](#id-section10)
- Capítulo 11: [](#id-section11)
- Capítulo 12: [](#id-section12)
- Capítulo 13: [](#id-section13)
- Capítulo 14: [](#id-section14)
- Capítulo 15: [](#id-section15)
- Capítulo 16: [](#id-section16)

<div id='id-section1'/>

## Capítulo 1

* Instalación de Python, de pyenv, django, git y recomendaciones sobre elegir un editor de código.
* Generar un entorno, empezando un proyecto y llamar a la carpeta 'Django'


<div id='id-section2'/>

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


<div id='id-section3'/>


## Capítulo 3

En el capítulo creará una app llamada Pages que tiene su propia homepage y un página about.

* Crear carpeta pages, entorno pipenv, startproject y startapp

* Añadir la aplicación pages al archivo settings.py



### Plantillas

Las plantillas (templates) generan archivos HTML.

Con Django constantemente se editan y crean estos tres elementos: 
- URLs: es donde se enruta dentro de la página.
- Views: contienen la lógica de qué sucede en ellos.
- Plantilla: contiene el HTML.

A nivel organizativo se puede generar una carpeta 'templates' con carpetas para cada app. Pero el enfoque que sigue en el libro es el de generar una única carpeta 'templates' a nivel de proyecto para todas las apps.

* Se crea una carpeta templates y dentro un archivo home.html
* Se edita el archivo settings.py para que contenga la carpeta creada dentro de la sección TEMPLATES y en 'DIRS.
* Se le añade un h1 al archivo html

### Views basadas en clases
Las views se realizan mediante clases. Al principio de Django, tenía un enfoque de funciones, pero se le añadió un enfoque basado en clases para evitar repetir código innecesario.

* Se añade el módulo TemplateView al archivo views y se le agrega la plantilla creada a la clase HomePageView

### Urls 
 Después se tienen que editar las URLs

* Se actualiza el urls.py a nivel de proyecto
* Se le añade un archivo urls.py a la carpeta pages (pages/pages) a nivel de app.
* Se escribe dentro del urls.py a nivel de app y al estar basado en clases se le añade add_view() al final del nombre.

### Añadiendo una página About
De manera similar al archivo home.html se le suma una página about en un archivo about.html

* Se crea el archivo.html
* Se le añade un h1
* Se añade al pages/views.py
* Se añade al urls.py de la app

### Ampliando las plantillas
 
Con ellas se crea el contenido que se repite en cada página.

* Se crea el archivo base.html

Django tiene un pequeño lenguaje con etiquetas y lógica para crear plantillas. [Aquí está la documentación oficial][https://docs.djangoproject.com/en/2.1/ref/templates/builtins/#built-in-template-tags-and-filters]. También se pueden crear etiquetas personalizadas.

Para añadir enlaces URL se usa la siguiente etiqueta:
``` 
{% url 'home' %}
```
* Se añade la etiqueta con los enlaces URL de home y about en  base.html
* En el mismo archivo, también se añade:
```
{% block content %}
{% endblock content %}
```
Esto indica que plantillas hijo (plantillas anidadas) podrán sobreescribir ahí.

* Se añade código a home.html y about.html usando el método 'extend' que pondrá en relación las plantillas.

Con ello se ha hecho que se incluyan los enlaces de las URLs de las dos tanto en Home como en About.

### Tests

Para cualquier proyecto, es importante poder testear si funciona cada apartado, especialmente cuando son grandes. Django viene con herramientas prefijadas para testear las aplicaciones.

* Se añade código al archivo page/tests.py

Se usa la clase SimpleTestCase porque no estamos usando base de datos. Con Base de datos se usa TestCase.
* Se ejecuta el test

### Git y Bitbucket
* Se genera el repositorio local y se sube a bitbucket


### Local vs Producción

Hasta ahora el contenido estaba de manera local en el dispositivo, se podía ver mediante localhost. A hacer un deploy en un servidor externo se le denomina ponerlo en producción. Para ello se usará Heroku.

### Heroku

* Se crea una cuenta en Heroku
* Se instala Heroku’s Command Line Interface
* Logearse en Heroku desde el terminal


### Archivos adicionales

* Modificar Pipfile.lock y ejecutar $pipenv lock
* Hacer un archivo Procfile
* Instalar gunicorn como servidor web
* Cambiar aone-line al archivo settings.py


### Deploy



#### Conclusión

