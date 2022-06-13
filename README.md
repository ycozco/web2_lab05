#PS_LABS
# INFORME DE LABORATORIO 04
<div align="center">
<table>
    <theader>
        <tr>
                <td style="width:50%; height:auto"><img src="https://github.com/ycozco/unsa_fisic_comp/blob/main/img/epis.png?raw=true" alt="EPIS" style="width:50%; height:auto"/></td>
            <th>
                <span style="font-weight:bold;">UNIVERSIDAD NACIONAL DE SAN AUGUSTIN</span><br />
                <span style="font-weight:bold;">FACULTAD DE INGENIERÍA DE PRODUCCIÓN Y SERVICIOS</span><br />
                <span style="font-weight:bold;">ESCUELA PROFESIONAL DE INGENIERÍA DE SISTEMAS</span>
            </th>
               <td><img src="https://github.com/ycozco/unsa_fisic_comp/blob/main/img/abet.png?raw=true" alt="ABET" style="width:50%; height:auto"/></td>
                  </tr>
    </theader>
    <tbody>
        <tr><td colspan="3"><span style="font-weight:bold;">Formato</span>: Guía del Estudiante / Talleres / Centros de Simulación</td></tr>
        <tr><td><span style="font-weight:bold;">Aprobación</span>:  2022/03/01</td><td><span style="font-weight:bold;">Código</span>: GUIA-PRLD-001</td><td><span style="font-weight:bold;">Página</span>: 1</td></tr>
    </tbody>
</table>
</div>

<div align="center">
<span style="font-weight:bold;">GUÍA DEL ESTUDIANTE</span><br />
<span>(formato del estudiante)</span>
</div>


<table>
<theader>
<tr><th colspan="6">INFORMACIÓN BÁSICA</th></tr>
</theader>
<tbody>
<tr><td>ASIGNATURA:</td><td colspan="5">Programación de Sistemas</td></tr>
<tr><td>TÍTULO DE LA PRÁCTICA:</td><td colspan="5">Punteros</td></tr>
<tr>
<td>NÚMERO DE PRÁCTICA:</td><td>06</td><td>AÑO LECTIVO:</td><td>2022 A</td><td>NRO. SEMESTRE:</td><td>III</td>
</tr>
<tr>
<tr> <td>Tipo de Practica</td>
    <td>Grupal</td><td>X</td>
        <td>Individual</td><td>Maximo de estudiantes</td><td></td>
    </td> 
</tr>

<td>FECHA INICIO::</td><td>Jun-2022</td><td>FECHA FIN:</td><td>11-Jun-2022</td><td>DURACIÓN:</td><td>04 horas</td>
</tr>
<tr><td colspan="6">INTEGRANTES:
<ul>
<li>Cozco Mauri Yoset -------------------- ycozco@unsa.edu.pe</li>
<li>Garay Bedregal César Alejandro -------- cgarayb@unsa.edu.pe</li>
<li>Sulla Quispe Vladimir ----------------- vsullaq@unsa.edu.pe</li>
</ul>
</td>
</<tr>
<tr><td colspan="6">DOCENTES:
<ul>
<li> Edson Francisco Luque Mamani(eluquem@unsa.edu.pe)</li>
</ul>
</td>
</<tr>
</tdbody>
</table>




<table>
<theader>
<tr><th colspan="6">SOLUCIÓN Y RESULTADOS</th></tr>
</theader>
<tbody>
</tr>
<tr><td colspan="6">
<tr>

## I. SOLUCIÓN DE EJERCICIOS PROPUESTOS:
<br>
<tr>
- Crea un blog sencillo en un entorno virtual utilizando la guía: https://tutorial.djangogirls.org/es/django_start_project/. 
- Especificar paso a paso la creación del blog en su informe.

## Entorno Virtual y Configuracion

- Lo primero que debemos tener en cuenta es activar nuestro entorno virtual de trabajo, para poder instalar librerias sin afectar a otros proyectos.

```bash
ncnc@ncnc:~/Desktop/test$ source ./bin/activate
(test) ncnc@ncnc:~/Desktop/test$
```
- Lo siguiente es instalar Django  par alo cual ejecutamos 

```bash
(test_2) ncnc@ncnc: pip install Django
```
- Instalando Django y dando como resultado:
```bash
(test_2) ncnc@ncnc:~/Desktop/test_2$ pip install Django
Collecting Django
  Using cached Django-4.0.5-py3-none-any.whl (8.0 MB)
Collecting asgiref<4,>=3.4.1
  Using cached asgiref-3.5.2-py3-none-any.whl (22 kB)
Collecting sqlparse>=0.2.2
  Using cached sqlparse-0.4.2-py3-none-any.whl (42 kB)
Installing collected packages: sqlparse, asgiref, Django
Successfully installed Django-4.0.5 asgiref-3.5.2 sqlparse-0.4.2

```

- Tenemos el siguiente resultado dado que previamente ya se ha instalado Djando en otra, carpeta
  Usa los archivos que tiene en Cache, caso contrario deberia descargar.

- Una ves instalado Django, debemos iniciar nuestro proyecto de la siguiente manera

```bash
django-admin startproject blog

```
- Tendriamos un resultado:

```bash
blog
├── manage.py
└── blog
    ├── asgi.py
    ├── __init__.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```
lo siguiente es crear el modelo de nuestro blog, este esta ubicado en la carpeta ```blog/models.py```

```python
from django.conf import settings
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(
            default=timezone.now)
    published_date = models.DateTimeField(
            blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
```
- como podemos observar el modelo de Post tiene los siguientes atributos:
    -  author: es una clave foranea que hace referencia a la tabla de usuarios
    -  title: es un atributo de tipo cadena de caracteres con una longitud maxima de 200 caracteres
    -  text: es un atributo de tipo cadena de caracteres
    -  created_date: es un atributo de tipo fecha y hora
    -  published_date: es un atributo de tipo fecha y hora
- Despues de esto tenemos que registrar nuestro modelo dentro de admin.py que se ubica en ```blog/admin.py```

```python
from django.contrib import admin
# Register your models here.
from .models import Post

admin.site.register(Post)
```
- Deberia quedar asi nuestro archivo ```admin.py```
- El siguiente paso es agregar como una aplicacion instalada en el archivo mysite/settings.py
</tr>
<tr>

-   Escriba el script ambito.sh, que modifique la variable de ambiente PATH, agregándole un par de rutas. El
programa deberá imprimir el valor de la variable PATH antes y después del cambio.
    
```bash
#!/bin/bash
echo "PATH antes de cambiar: $PATH"
export PATH=$PATH:/home/user/bin:/home/user/bin/subdir
echo "PATH después de cambiar: $PATH"
```

</tr>

<tr> 

-   Escriba el script dosArgumentos.sh que reciba dos argumentos y los muestre en la salida estándar, si el script
recibe una cantidad distinta de argumentos deberá mostrar un mensaje de error y terminar su ejecución.
Este ejercicio lo puede resolver con if, then, else ó con sólo if, then y usando return para terminar la
ejecución del programa.
        
```bash
#!/bin/bash
if [ $# -eq 2 ]
then
    echo "El primer argumento es $1 y el segundo es $2"
else
    echo "Error: Cantidad de argumentos incorrecta"
fi
```
</td><tr>
-   Usted deberá escribir un script que reciba dos argumentos, cada argumento será una lista de valores. El primer
    argumento contendrá una lista de palabras, el segundo argumento contendrá una lista de archivos de texto.
    Su programa deberá usar el programa grep o ed, para buscar cada una de las palabras en cada uno de los
    archivos, reportando las líneas en que las palabras fueron encontradas. A continuación se muestra un
    ejemplo de su funcionamiento:
    
```bash 
$ index.sh "los sangre escribir" "poema20.txt cantocoral.txt"
los
poema20.txt: 1 4 8 17 32 34 49
cantocoral.txt: 12 17 25 39
sangre
poema20.txt:
cantocoral.txt: 11
escribir
poema20.txt: 1 8 17
cantocoral.txt:
```

Usted deberá incluir todos los experimentos que le ayudaron a resolver este problema, por lo que deberá
hacer tantos commits como sean necesarios. Sin esos experimentos que demuestren cómo resolvió el
problema, no tendrá nota.
Puede usar estos archivos, para probar su programa: <br>
● https://drive.google.com/file/d/1EphGW4yHMlV2XVv0GHe4eu8nFnHIbydL/view?usp=sharing <br>
● https://drive.google.com/file/d/1dumtV1ReByIVVCqy86l2AyGUYS3dB0qw/view?usp=sharing


```bash
#!/bin/bash
for keyword in $1
do
  printf "%s\n" $keyword
  for file in $2
  do
    RES=`grep -n $keyword $file|cut -d":" -f1|tr "\n" " "`
    printf "\t%s:\t%s\n" $file "$RES"
  done
done
```

</tr>


<tr><td colspan="6">II. SOLUCIÓN DE CUESTIONARIO: <br>

- Ejecute el programa ambito.sh y luego verifique el valor de la variable PATH desde línea de comandos. ¿Qué
puede concluir de este experimento?
Se concateno el nuevo valor entregado por el usuario al valor original de la variable PATH.
Al modificar la variable PATH, podemos actualizar el valor tanto borrando o concatenando nuevos valores.

![Ejercicio2_d](images/ambito.sh.png)

</tr>
</tr>
<tr><td colspan="6">III. CONCLUSIONES:

</tr>

</tdbody>
</table>


<table>
<theader>
<tr><th colspan="6">RETROALIMENTACIÓN GENERAL</th></tr>
</theader>
<tbody>
</tr>
<tr><td colspan="6">
<ul>
<li><a </a></li>
<li><a </a></li>
<li><a </a></li>
</ul>
</td>
</<tr>
</tdbody>
</table>


<table>
<theader>
<tr><th colspan="6">REFERENCIAS BIBLIOGRÁFICAS</th></tr>
</theader>
<tbody>
</tr>
<tr><td colspan="6">
<ul>
<li>Cannon Jason, Shell Scripting: How to Automate Command Line Tasks Using Bash Scripting and Shell
Programming. 2015.</li>


<li></li>
</ul>
</td>
</<tr>
</tdbody>
</table>


