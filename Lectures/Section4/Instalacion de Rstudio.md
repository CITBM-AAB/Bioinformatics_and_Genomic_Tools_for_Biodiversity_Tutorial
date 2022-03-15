## Instalación de Rstudio

Para programar en R y realizar análisis de datos no es aconsejable ni práctico trabajar con la consola de R sino que es necesario disponer de una interfaz más visual, como RStudio, que es un entorno de desarrollo integrado (IDE) de R que incluye diferentes herramientas, como la consola, un editor de código y otros elementos de depuración

* **Descarga Rstudio para Linux, Windows o Macos** (https://www.rstudio.com/products/rstudio/download/#download)

![image](https://github.com/bioinfoperu/Introduccion-a-R-y-Rstudio/blob/main/img/Rstudio_interfaz.png)

* **Interfaz de Rstudio**

La interfaz se divide en cuatro ventanas, las de la izquierda correspen al espacio de trabajo y las de la derecha nos dan información sobre los diferentes con los que se trabajarán, paquetes instalados e información general de R. 

Para comenzar a trabajar con R desde Rstudio, abriremos el programa y ejecutaremos _File > New File > R Script_. En este momento visualizaremos cuatro ventanas en la interfaz de Rstudio. Escribiremo código en el espacio de trabajo y presionando el boton de _Run_ o _Ctrl + R_, ejecutaremos la linea o lineas del código R. Los resultados los visualizaremos en la ventan inferior, este espacio se le denimona **modo consola**.

El script que escribiremos lo guardaremos en _File > Save As_, el cual nos dará in archivo con extensión _.R_.

**¡Bien!**

Ante de empezar tenemos que ubicar los archivos de trabajo. Para ello, realizaremos lo siguiente _Session > Set working directory > Choose Directory_. Tambien la función _setwd("directorio")_ permite cambiar la ubicació de los archivos. 

En caso que requerimos ayuda podemos presionar la pestaña **_Help_** del panel derecho. Tambien podemos ejecutar la función precediendola del simbolo _?_. Ejemplo:

**?print**

## Entorno de trabajo de RStudio

* Permite cambiar la ubicación de los archivos

```
setwd() 
```

* Visualizar la ayuda sobre una determinada función

```
?print 
```

```
help()

```

### **Ejercicio 1**

```{r}
print("Este es mi primer Script en R")
