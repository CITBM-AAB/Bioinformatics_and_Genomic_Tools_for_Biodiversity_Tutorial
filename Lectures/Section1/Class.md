# intro_terminal
## Introducción a Unix y la SHELL

### Resumen

Práctico para entender UNIX/Linux


### Introducción

Unix/Linux es el sistema operativo estándar para computo científico. Algo similar sucede con Windows, pero en computadores de escritorio (PC).

Siguiendo esta comparativa, las similitudes entre ambos Sistemas Operativos son:

  - Se encargan de manejar el hardware por ud (redes, discos duros, procesador).

  - Proveen una interfaz para ejecutar aplicaciones y almacenar sus archivos.

  - Ambos poseen interfaces de escritorio que ofrecen casi las mismas prestaciones.


Por otra parte, Unix es seguro, estable y permite la ejecución de tareas con múltiples usuarios. Esto lo ha transformado en el sistema operativo de excelencia para computación de alto rendimiento (HPC: High Performance Computing). Se puede utilizar en diferentes tipos de hardware desde RaspberryPi, celulares y tablets (Android), notebook y PC hasta supercomputadores como Leftraru del [NLHPC](http://www.nlhpc.cl).

### Puesta a punto


Para facilitar este y los demás prácticos, he habilitado una de mis máquinas para la ejecución de tareas en este curso.

Además, en prácticos posteriores, algunos de los cálculos que realizaremos requeriran de un poder de cómputo moderado.  Por esto nos conectaremos a un servidor personal que puede ejecutar estas tareas. 

Para esto necesitaremos una conexión a internet.

Si están en:

  - *Linux/MacOS*, puede utilizar [la terminal](https://help.ubuntu.com/kubuntu/desktopguide/es/terminals.html) (consola).

  - *Windows10* utilice el [Símbolo del sistema](https://es.wikipedia.org/wiki/S%C3%ADmbolo_del_sistema) (`cmd`).

  - Si están en *Windows* (anterior a *Windows 10*) deben instalar un programa llamado [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).


### La Terminal

  - Es llamada *prompt*, *shell*, *línea de comandos*.

  - Antiguamente, era la única forma de interactuar con los computadores. 
  
  - La terminal es bastante agreste!.
 
  - Hablando en serio, es la interfaz que se utiliza para ejecutar comandos/programas o analizar los datos.

  - La mayoría de los programas que utilizamos a diario tienen una [GUI](https://es.wikipedia.org/wiki/Interfaz_gr%C3%A1fica_de_usuario)(Graphical User Interface). Sin embargo, la mayoría de los programas más utilizados en Bioinformática genómica no poseen una interfaz gráfica, esto principalmente porque los servidores donde se ejecutan los programas no tienen GUI, además de que requiere una etapa adiciónal de diseño y presupuesto que no justifica para la aplicación.

  - Saber utilizar la terminal nos proveerá de una cantidad sustancial de ventajas en HPC.

### Protocolo SSH

Ahora, en la terminal, utilizaremos el protocolo [SSH](https://web.mit.edu/rhel-doc/4/RH-DOCS/rhel-rg-es-4/ch-ssh.html).

> :warning:  **NOTA**: De ahora en adelante, cada vez que vea `instrucción` se referira a un comando/programa a ejecutar, mientras que:

		esto será código a escribir en la terminal

> :warning: **NOTA**: En *Unix*, la terminal es *case sensitive*, es decir, escribir una `instrucción` es distinto a escribir  una `INSTRUCCIÓN` o `Instrucción` (*Windows* es diferente). Lo mismo pasa con los usuarios y los nombres de archivos. 

> :warning: **NOTA**: La mayoría de las veces, cuando tenga un problema al ejecutar una instrucción, se debe a errores tipográficos (*typos*). 
 
Una vez abierta la terminal (solo en *Win10*, *Linux*, *MacOS*), cada grupo debe escribir lo siguiente:

         ssh  usuario@servidor


> :warning: **NOTA**: Las credenciales se les entregaran en la pizarra.


Mediante el comando SSH podremos entrar al servidor para el curso. 

### Estructura de Directorios

En linux los directorios se organizan en una Jerarquía, es decir hay un directorio raíz y desde ese directorio se accede a sub-directorios.

Recordemos la estructura de directorios en LINUX.

Dentro del servidor podemos ver donde estamos ubicados utilizando `pwd` ([print working directory](https://linux.die.net/man/1/pwd)). 

		pwd

Para saber el contenido del directorio donde estamos ubicados utilizamos `ls` ([list](https://linux.die.net/man/1/ls))


		ls

Si tenemos más de un directorio podemos ingresar a ese directorio con el comando `cd` ([change directory](http://linuxcommand.org/lc3_man_pages/cdh.html))

		cd ejemplo

### Revisar Archivos


Podemos mirar (Read Only) archivos con varios comandos como por ejemplo `more` ([man more](https://linux.die.net/man/1/more)):


		more secuencia.fna

También está el comando `less` ([man less](https://linux.die.net/man/1/less)):

		less secuencia.fna


Hay diferencias?.

Otro comando es `cat` ([man cat](https://linux.die.net/man/1/cat)):


		cat secuencia.fna

> :warning: **NOTA** `cat` es utilizado para concatenar archivos.



> :star: **HACK**:  Cuando quiere escribir un comando o buscar un directorio o escribir el nombre de un archivo, puede utilizar autocompletar con la tecla tab. [Link](https://i.ytimg.com/vi/KEkrWRHCDQU/hqdefault.jpg)


Probemos con el siguiente comando `head`:

		head secuencia.fna

o con el comando `tail`:

		tail secuencia.fna

Saber el número de palabras:

		wc secuencia.fna

Saber el número de lineas:

		wc -l secuencia.fna


### Manual

La mayoria de las aplicaciones en Unix tienen una página en el manual de linux `man`, incluso el comando man tiene us propia página en el manual.

		man man 

Con esto es posible parametrizar su aplicación.


Por ejemplo veamos la página del manual para el comando `head`


		man head


¿Qué le imprimirá el siguiente comando?:

		head -n 1 secuencia.fna 


### Revisión de archivos Parte 2 (Edición)


Existen diferentes editores de texto para la terminal, uno de los más poderoso es [vim](https://www.vim.org/).

		vim holamundo.txt


Apareceremos en el editor y las teclas de nuestro teclado ahora serán comandos del editor. Para salir del modo comando es necesario apretar la tecla `i`, esta nos llevará al modo -INSERTAR-. Ahora puede insertar texto, escribiremos:

		HOLA MUNDO

Para salir del modo -INSERTAR- y volver al modo comando apretaremos la tecla `Esc`. luego apretaremos la tecla `:`
y escribiremos:

		wq!

Esto significa write (w) quit (q) and no questions (!).


Haremos algunos otros ejemplos.


### Revisión de Archivos Parte 3 (Búsqueda de expresiones).

En el caso de que necesitaramos buscar o extraer información desde un archivo, podemos utilizar el comando `grep` ([Globally search for a Regular Expression and Print](https://linux.die.net/man/1/grep)). Primero veremos lo que hace `grep` luego veremos las *expresiones regulares* ([Regular Expressions](https://es.wikipedia.org/wiki/Expresi%C3%B3n_regular)).

Para este caso utilizaremos el archivo [GFF3](https://github.com/The-Sequence-Ontology/Specifications/blob/master/gff3.md) que fue descargado desde [NCBI - GenBank](https://www.ncbi.nlm.nih.gov/genbank/).

		less secuencia.gff3

Veremos que este archivo posee varias columnas y filas, supongamos que queremos capturar las filas que tienen la palabra pseudogene

		grep "pseudogene" secuencia.gff3

Supongamos que ahora queremos contar cuantas lineas/filas tienen la palabra pseudogene. Podemos revisar utilizando man o ejecutando grep --help si es que grep tiene una opción que nos permita realizar este cálculo:

		grep --help


Como vemos la opción -c o --count nos permite contar las lineas que cumplen con el patrón de búsqueda:

		grep --count "pseudogene" secuencia.gff3

Ejecutar:

		grep -c "pseudogene" secuencia.gff3

Es diferente?

Es concordante con la información mostrada en NCBI para ese [genoma](https://www.ncbi.nlm.nih.gov/genome/?term=Piscirickettsia%20salmonis)?


### PIPES

Una de las funcionalidades más potente de unix es la concatenación de instrucciones, más conocido como pipelines. Supongamos que queremos saber solo los pseudogenes que estan presentes en el cromosoma de la bacteria y no en sus plasmidios.

Podemos utilizar la concatenación de dos grep:

		grep "pseudogene" secuencia.gff3 | grep "NZ_CP011849"

Qué pasó?

Si utilizamos:

		
		grep -c "pseudogene" secuencia.gff3 | grep "NZ_CP011849"

Cuánto da el resultado?

y si utilizamos:

		
		grep "pseudogene" secuencia.gff3 | grep -c "NZ_CP011849"

Cuánto da el resultado?


Por qué son distintos?, es concordante con lo presentado en NCBI?


### Expresiones regulares:


Supongamos que ahora queremos contar los genes en el archivo gff que pertenecen al cromosoma, ejecutemos:


		grep "gene" secuencia.gff3 | grep -c "NZ_CP011849"

Es concordante con lo presentado en NCBI?.

Qué pasó?


Que pasa si ejecutamos:


		grep $'\tgene' secuencia.gff3 | grep -c "NZ_CP011849"

Es el mismo resultado que en:

		grep $'\tgene' secuencia.gff3 | grep "NZ_CP011849" | wc -l


Por qué?


## PARTE II 


### Revisión de un archivo FASTQ.



Los archivos [FASTQ](https://en.wikipedia.org/wiki/FASTQ_format), son archivos de texto que almacenan las secuencias nucleotídicas que provienen de una secuenciación
y sus valores de calidad correspondientes en formato [ASCII](https://es.wikipedia.org/wiki/ASCII). 
Actualmente se utiliza el código [ASCII partiendo desde el valor 33](https://support.illumina.com/help/BaseSpace_OLH_009008/Content/Source/Informatics/BS/QualityScoreEncoding_swBS.htm).

La calidad de los archivos FASTQ es el mapeo a un valor entero de la probabilidad de error en la lectura de un nucleótido por parte de la máquina.

Este es el valor [PHRED](https://genome.cshlp.org/content/8/3/186.short)

A continuación podemos ver una tabla de resumen de las calidades Phred y la probabilidad de error:

| Valor Phred| Probabilidad de base errónea | Precisión |
| ----- | ---- |----|
| 10 | 1 en 10 | 90% |
| 20 | 1 en 100 | 99% |
| 30 | 1 en 1000 | 99.9% |
| 40 | 1 en 10000 | 99.99% |
| 50 | 1 en 100000 | 99.999% |


Utilizaremos el programa [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/). FastQC nos muestra estadísticas sobre nuestros resultados de secuenciación.


Revisemos nuestro archivo con el comando `fastqc`:


		fastqc 


Ahora revisaremos cada uno de los campos en el siguiente [link](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/):


Ahora ejecutaremos `fastqc` sin GUI, entraremos al help:

		fastqc --help


Ejecutaremos todo:

		fastqc SRR18080892.fastq


Ahora desde nuestro computador abrimos una terminal y nos traemos el informe utilizando SCP:


		scp usuario@servidor:ejercicio/SRR18080892_fastqc.zip .  


Ahora en su computador extraiga su archivo y veamos el archivo.


Cómo explica el problema de la baja de calidad al final de los reads? Hint1: Phasing [Hint2](https://www.nature.com/articles/nbt.1585)


------Ejercicio:-------------------
Es muy importante que para la próxima clase de High Performance Computing, ya sea capaz de saber acceder a un servidor mediante SSH y pueda crear y editar archivos mediante `vi` o `nano`. Además, cuando uno quiere tener estadísticas rápidas de las secuencias biológicas, son muy útiles las expresiones regulares y el comando grep.

Por esto:

1. Vuelva a ejecutar toda el práctico de nuevo hasta que se sienta capaz de dominar la terminal.
2. Escriba una pequeña reseña sobre usted utilizando `vi` en un archivo llamado APELLIDONOMBRE_VIM.txt (Donde APELLIDO es su apellido y NOMBRE es su nombre).
3. Escriba la misma reseña sobre usted, pero utilizando `nano` llamado APELLIDONOMBRE_NANO.txt (Donde APELLIDO es su apellido y NOMBRE es su nombre).







