## Importación y exportación de archivos

* Importar archivo de texto (*.txt)

```{r}
student_txt = read.table("/home/mars/Documents/UoC/SAD_LAB1_datos/student-mat.txt")
head(student_txt) # Muestra las primera lineas
```

* Importar archivo de texto en forma de tabla (*.csv)

```{r}
student_csv = read.csv("/home/mars/Documents/UoC/SAD_LAB1_datos/student-mat.csv", header = TRUE,  sep = ";")
head(student_csv)
```

```{r}
student_csv2 = read.csv2("/home/mars/Documents/UoC/SAD_LAB1_datos/student-mat.csv")
head(student_csv2)
```

* Importar archivo tipo hoja de cálculo Excel (*.xlsx)

```{r}
install.packages(c("readxl", "xlsx"))
library("readxl")
library("xlsx") # Requiere que se instale Java
```

```{r}
student_xlsx = read_xlsx("/home/mars/Documents/UoC/SAD_LAB1_datos/student-mat.xlsx")
head(student_xlsx)
```

* Importar archivos procedentes de SPSS ("*.sav")/STATA(".dta")

```{r}
# Instalaremos el paquete foreign
install.packages("foreign") 
library("foreign")
```

```{r}
student_sav = read.spss("/home/mars/Documents/UoC/SAD_LAB1_datos/student-mat.sav")
head(student_sav) 
```

## **Ejercicio 3**

* Importar archivo de texto (*.txt)

```{r}
data_txt = read.table("/home/mars/Documents/UoC/SAD_LAB1_datos/dataBreastCancer.txt")
head(data_txt) 
```

* Importar archivo de texto en forma de tabla (*.csv)

```{r}
student_csv = read.csv("/home/mars/Documents/UoC/SAD_LAB1_datos/wisc_bc_data.csv")
head(student_csv)
```

* Importar archivos procedentes de SPSS ("*.sav")/STATA(".dta")

```{r}
library(foreign)
student_sav = read.spss("/home/mars/Documents/UoC/SAD_LAB1_datos/student-mat.sav")
head(student_sav) 
```

## Exportar desde R

* Exportar datos a archivos de tipo texto (*.txt):

```
write.table(mydata,"/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.txt", sep = "")
```

* Exportar datos a archivos de tipo *.csv:

```
write.csv(mydata, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.csv")
```

* Exportar datos a archivos de tipo *.xlsx:

```
library(xlsx)
write.xlsx(mydata, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.xlsx")
```

* Exportar datos a archivos de tipo SPSS:

```
write.foreign(mydata, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss.txt", "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss", package = "SPSS")
```

* Exportar datos a archivos de tipo SPSS:

```
write.foreign(mydata, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss.txt", "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss", package = "SPSS")
```

* Exportar datos a archivos de tipo SAS:

```
write.foreign(mydata, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss.txt", "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss", package = "SPSS")
```

* Exportar datos a archivos de tipo STATA:

```
write.dta(mydata, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.dta")
```

* Trabajaremos con el paquete _MASS_ y cargaremos los datos de _biopsy_

```{r}
library(MASS)
data("biopsy")
head(biopsy)
```

* Exportar datos a archivos de tipo texto (*.txt):
```{r}
write.table(biopsy,"/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.txt", sep = "")
```

* Exportar datos a archivos de tipo *.csv:

```{r}
write.csv(biopsy, file = "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.csv")
```

* Exportar datos a archivos de tipo *.xlsx:

```{r}
write.xlsx(biopsy, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.xlsx")
```

* Exportar datos a archivos de tipo SPSS:

```{r}
write.foreign(biopsy, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss.txt", "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.spss", package = "SPSS")
```

* Exportar datos a archivos de tipo STATA:

```{r}
write.dta(biopsy, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata.dta")
```

## **Ejercicio 4**

```{r}
library(MASS)
data("Melanoma")
head(Melanoma)
```

* Exportar datos a archivos de tipo texto (*.txt):

```{r}
write.table(Melanoma,"/home/mars/Documents/UoC/SAD_LAB1_datos/mydata_melanoma.txt", sep = "")
```

* Exportar datos a archivos de tipo *.csv:

```{r}
write.csv(Melanoma, file = "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata_melanoma.csv")
```

* Exportar datos a archivos de tipo *.xlsx:

```{r}
write.xlsx(Melanoma, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata_melanoma.xlsx")
```

* Exportar datos a archivos de tipo SPSS:

```{r}
write.foreign(Melanoma, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata_melanoma.txt", "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata_melanoma.spss", package = "SPSS")
```

* Exportar datos a archivos de tipo STATA:

```{r}
write.dta(Melanoma, "/home/mars/Documents/UoC/SAD_LAB1_datos/mydata_melanoma.dta")
```
