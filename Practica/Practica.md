# Entorno de desarrollo y producción con aplicaciones web python

**Tarea 1: Entorno de desarrollo**
Formas parte del equipo de desarrollo de la aplicación “Gestión IESGN”, aplicación web desarrollada con python, con el framework django. Vamos a configurar tu equipo como entorno de desarrollo para trabajar con la aplicación, para ello:
- Realiza un fork del repositorio de GitHub: https://github.com/jd-iesgn/iaw_gestionGN.

[Repositorio](https://github.com/PalomaR88/iaw_gestionGN)

- Clona el repositorio en tu equipo.
~~~
paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB$ git clone git@github.com:PalomaR88/iaw_gestionGN.git
~~~

- Crea un entorno virtual python3 e instala las dependencias necesarias para que funcione el proyecto (fichero requierements.txt).
Creación del entorno:
~~~
paloma@coatlicue:~/DISCO2$ mkdir virtualenv
paloma@coatlicue:~/DISCO2$ cd virtualenv/
paloma@coatlicue:~/DISCO2/virtualenv$ python3 -m venv django
paloma@coatlicue:~/DISCO2/virtualenv$ source django/bin/activate
~~~

Instalación de los paquetes:
~~~
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ pip install -r requirements.txt 
~~~

En la instalación de los paquetes que aparecen en requirements.txt surgen errores que hay que solucionar:
~~~
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ sudo apt install python3-dev
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ pip3 install wheel
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ sudo apt install libjpeg-dev
~~~

Este debe de ser el rescultado:
~~~
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ pip freeze
Django==1.10.2
html5lib==1.0b8
olefile==0.46
Pillow==4.0.0
pkg-resources==0.0.0
PyPDF2==1.26.0
pytz==2019.3
reportlab==3.3.0
six==1.10.0
sqlparse==0.3.0
webencodings==0.5
xhtml2pdf==0.0.6
~~~


- Comprueba que vamos a trabajar con una base de datos sqlite (gestion\settings.py). ¿Cómo se llama la base de datos que vamos a crear?
~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
~~~


- Crea la base de datos: python3 manage.py migrate. A partir del modelo de datos se crean las tablas de la base de datos.
~~~
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ python3 manage.py migrate
Operations to perform:
  Apply all migrations: admin, auth, centro, contenttypes, convivencia, sessions
Running migrations:
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying centro.0001_initial... OK
  Applying centro.0002_cursos_equipoeducativo... OK
  Applying centro.0003_auto_20161102_1656... OK
  Applying centro.0004_auto_20161102_1721... OK
  Applying centro.0005_auto_20161105_1217... OK
  Applying centro.0006_auto_20161106_1741... OK
  Applying convivencia.0001_initial... OK
  Applying sessions.0001_initial... OK
~~~


- Añade los datos de prueba a la base de datos. Para más información: https://coderwall.com/p/mvsoyg/django-dumpdata-and-loaddata. Utiliza el fichero datos.json.
~~~
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ ./manage.py loaddata datos.json 
Installed 89 object(s) from 1 fixture(s)
~~~

- Entra en la zona de administración para comprobar que los datos se han añadido correctamente. Usuario: admin contraseña: asdasd1234).

Se ejecuta el servidor web:
~~~
(django) paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES W
EB/iaw_gestionGN$ python manage.py runserver
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).
November 21, 2019 - 19:57:57
Django version 2.2.7, using settings 'gestion.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
~~~

Y en la nueva página 

- Ejecuta el servidor web de desarrollo y comprueba en el navegador que la aplicación está funcionando. Accede con el usuario usuario (contraseña: asdasd1234).









En este momento, muestra al profesor la aplicación funcionando. Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea. (3 puntos)


**Tarea 2: Desarrollando nuestra aplicación**

Vamos a realizar un cambio en la aplicación y comprobar que los cambios se realizan correctamente.
- Modifica la página inicial de la aplicación para que aparezca tu nombre.

- Sube los cambios al repositorio

Muestra una captura de pantalla donde sea la modificación realizada. (1 punto)


**Tarea 3: Entorno de producción**

Vamos a realizar el despliegue de nuestra aplicación en un entorno de producción, para ello vamos a utilizar una instancia del cloud, para ello:

- Instala en el servidor los servicios necesarios (apache2, mysql, …). Instala el módulo de apache2 para ejecutar código python.

- Clona tu repositorio en el DocumentRoot de tu virtualhost.

- Crea un entorno virtual e instala las dependencias de tu aplicación.

- Instala el módulo que permite que python trabaje con mysql:
~~~
      $ apt-get install python3-mysqldb
~~~

- Y en el entorno virtual:
~~~
      (env)$ pip install mysql-connector-python
~~~

- Configura un virtualhost en apache2 con la configuración adecuada para que funcione la aplicación. El punto de entrada de nuestro servidor será iaw_gestionGN/gestion/wsgi.py.

- Crea una base de datos y un usuario en mysql.

- Configura la aplicación para trabajar con mysql, para ello modifica la configuración de la base de datos en el archivo settings.py:
~~~
      DATABASES = {
          'default': {
              'ENGINE': 'mysql.connector.django',
              'NAME': 'myproject',
              'USER': 'myprojectuser',
              'PASSWORD': 'password',
              'HOST': 'localhost',
              'PORT': '',
          }
      }
~~~

- Crea las tablas de la base de datos y carga los datos de pruebas. Accede a mysql y comprueba que se han creado de forma adecuada.

- Desactiva en la configuración (fichero settings.py) el modo debug a False. Para que los errores de ejecución no den información sensible de la aplicación.

- Muestra la página funcionando.

En este momento, muestra al profesor la aplicación funcionando. Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea. (4 puntos)


**Tarea 4: Modificación de la aplicación en el entorno de producción**

Vamos a realizar cambios en el entorno de desarrollo y posteriormente vamos a subirlas a producción.

- Modifica la página inicial para que muestre otra imagen. Despliega los cambios en el servidor de producción.

- Vamos a crear una nueva tabla en la base de datos, para ello sigue los siguientes pasos:
1. Añade un n uevo modelo al fichero centro/models.py:
~~~
     class Modulos(models.Model):	
         Abr = models.CharField(max_length=4)
         Nombre = models.CharField(max_length=50)
         Unidad = models.ForeignKey(Cursos,blank=True,null=True,on_delete=models.SET_NULL)
    		
         def __unicode__(self):
             return self.Abr+" - "+self.Nombre 		

         class Meta:
             verbose_name="Modulo"
             verbose_name_plural="Modulos"
~~~

2. Crea una nueva migración: python3 manage.py makemigrations.

3. Y realiza la migración: python3 manage.py migrate

4. Añade el nuevo modelo al sitio de administración de django:

- Para ello cambia la siguiente línea en el fichero centro/admin.py:
~~~
from centro.models import Cursos,Alumnos,Departamentos,Profesores,Areas
~~~

Por esta otra:
~~~
from centro.models import Cursos,Alumnos,Departamentos,Profesores,Areas,Modulos
~~~

Y añade al final la siguiente línea:
~~~
admin.site.register(Modulos)
~~~

- Despliega el cambio producido al crear la nueva tabla en el entorno de producción.

Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea. En este momento, muestra al profesor la aplicación funcionando en el otro hosting. (4 puntos)

**Tarea 5: Despliegue de nuestra aplicación en un hosting python: pythonanywhere**

- Siguiendo la documentación despliega nuestra aplicación django en pythonanwhere. Utiliza git para desplegar los ficheros y crea una base de datos en tu proyecto. Si con la documentación no es suficiente puede seguir mi documento: Despliegue de aplicación flask en hosting pythonanywhere.

Entrega una breve documentación donde expliques los pasos más importantes para el despliegue en pythonanywhere (3 puntos)

- Identificación de problemas: si estamos desarrollando una aplicación es necesario probarla, realizar test.

- Identificación de problemas: además de lo anterior el equipo de desarrollo necesita ir haciendo otros procesos: analizando el código generado, generar documentación,…

- Identificación de problemas: Nuestro equipo de desarrollo las componen varios miembros: es fundamental utilizar un repositorio común (git)

- Identificación de problemas: Si seguimos una metodología ágil es deseable que todos los cambios que vayan realizando los programadores se vayan probando, analizando, … de forma continúa

- Identificación de problemas: ¿Y si esas tareas las automatizamos? -> Integración continúa
