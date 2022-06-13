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
    <td>Grupal;</td><td>X</td>
        <td>Individual</td><td>Maximo de estudiantes</td><td></td>
    </td> 
</tr>

<td>FECHA INICIO::</td><td>Jun-2022</td><td>FECHA FIN:</td><td>11-Jun-2022</td><td>DURACIÓN:</td><td>04 horas</td>
</tr>
<tr><td colspan="6">ALUMNO:
<ul>
<li>Cozco Mauri Yoset (ycozco@unsa.edu.pe)</li>
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

## I. SOLUCIÓN DE EJERCICIOS PROBLEMAS:
<br>
<tr>
-   Las comillas invertidas permiten ejecutar programas dentro de los scripts y almacenar el resultado de
ejecución en variables. Escriba un script que reciba dos argumentos y que internamente llame al programa
grep con la opción -n (devuelve el número de línea de la ocurrencia), para luego mostrar el resultado del
comando grep. Es posible que el resultado de grep devuelva varias líneas, en ese caso la variable será una
lista de líneas, puede iterar sobre ella para mostrar cada línea por separado.
    
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


