## Gestión de paquetes

* Información de la version de R y paquetes cargados

```{r}
sessionInfo() 
```

* Información sobre los paquetes instalados en Rstudio y la ruta de ubicación

```
library() 
```

* Información sobre la ruta de la libreria

```{r}
.libPaths() 
```

* Lista los paquetes cargados

```{r}
search()
```

* Actualización de todos los paquetes existentes 

```
update.packages() 
```

* Instalación de paquetes adicionales

```
install.packages("paquete") 
```

* Instalación de más de un paquete

```
install.packages(c("paquete1","paquete2")) 
```

* Cargar el paquete especifico

```
library("paquete") 
```

### **Ejercicio 2**

```
# Instalaremos los paquetes _MASS_ y _survival_
install.packages("MASS")
library("MASS")
data(package="MASS") # Mostramos los elementos del paquete
```

```
install.packages("survival")
library("survival")
data(package="survival")
```
