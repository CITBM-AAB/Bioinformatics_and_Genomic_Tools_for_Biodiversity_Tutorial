## Tipos de datos, operadores y estructuras de datos en R 

```
library(MASS)
data(package="MASS")
data("birthwt")
head(birthwt)
```

* Descripción del conjunto de datos de birthwt del paquete MASS

```{r}
# Muestra el conjunto de datos en formato tabla
View(birthwt) 
```

```{r}
# Muestra el número de observaciones y el número de variables (filas y columnas)
dim(birthwt) 
```

```{r}
# Muestra el número de variables (Columnas)
length(birthwt) 
```

```{r}
# Muestra el nombre de las variables
names(birthwt) 
```

```{r}
# Muestra las primeras filas
head(birthwt) 
```

```{r}
# Muestra las últimas filas
tail(birthwt) 
```

```{r}
# Muestra un resumen de los parámetros estísticos más comunes
summary(birthwt) 
```

## **Ejercicio 5**

```
library(MASS)
data(package="MASS") # Mostramos los elementos del paquete
data("biopsy")
head(biopsy)
```

```{r}
# Muestra el conjunto de datos en formato tabla
View(biopsy) 
```

```{r}
# Muestra el número de observaciones y el número de variables (filas y columnas)
dim(biopsy) 
```

```{r}
# Muestra el número de variables (Columnas)
length(biopsy) 
```

```{r}
# Muestra el nombre de las variables
names(biopsy) 
```

```{r}
# Muestra las primeras filas
head(biopsy) 
```

```{r}
# Muestra las primeras filas
tail(biopsy) 
```

```{r}
# Muestra un resumen de los parámetros estísticos más comunes
summary(biopsy) 
```

## Constantes y Variables en R

```{r}
num <- 5
num
```

## Tipos de datos en R

* Númerico

* Cadena de texto

* Factor

* Lógico


* Estructura interna de las variables del conjunto de datos birthwt

```{r}
str(birthwt)
```

* Tipo de variables del conjunto de datos birthwt

```{r}
 # Conjunto de datos 
class(birthwt)
```

```{r}
# Variable age del conjunto de datos birthwt
class(birthwt$age) 
```

```{r}
# Variable race del conjunto de datos birthwt
class(birthwt$race) 
```

**Nota**: Para acceder a una variable del conjunto de datos utilizamos el simbolo $ 


```{r}
# Muestra los valores que toma la variable y nos da información de las variables y nos da la información de los niveles
factor(birthwt$race) 
```

```{r}
# 1 <- white, 2 <- black, 3 <- other
birthwt$race <- factor(birthwt$race, levels = c(1,2,3), labels = c("white","black","other")) 
birthwt$race
```
**Nota**: La expresión c(1,2,3) define lo que llamamos vector y que se explicará más adelante

```{r}
class(birthwt$race)
```

```{r}
# Comprobamos si existe valores NA
table(is.na(birthwt)) 
```

```{r}
# Comprobamos si existen valores NULL
table(is.null(birthwt)) 
```

* Creamos un data frame a partir de tres vectores

```{r}
a = c(2, 3, 5, 4)
s = c("aa", "bb", "cc", NA)
b = c(TRUE, FALSE, TRUE, FALSE)
df = data.frame(a,s,b)
```

```{r}
View(df)
```

```{r}
table(is.na(df))
```

```{r}
table(is.null(df))
```

* Lista de filas con datos que poseen datos perdidos

```{r}
df[complete.cases(df),] # Remueve filas con valores perdidos en cualquier columnda del data frame
```

* Crear un conjunto de datos sin contar los datos perdidos

```{r}
dfnew <- na.omit(df)
dfnew # En este caso no hay datos perdidos
```
**Nota:** En el ejemplo anterior se utilizan funciones, como data.frame(), que se explicarán más adelante

## **Ejericcio 6**

```{r}
data("anorexia")
head(anorexia)
```

```{r}
names(anorexia)
```

```{r}
table(is.na(anorexia$Treat))
```

```{r}
table(is.null(anorexia$Treat))
```

```{r}
anorexia$Treat
```

```{r}
anorexia$Treat <- factor(anorexia$Treat, levels = c("CBT", "Cont", "FT"), labels = c("Cogn Beh Tr","Contr","Fam Tr"))
anorexia$Treat
```

## Operadores en R

* Operadores de asignación

```{r}
num1 <- 10 # Asignar valor a una variable

num2 = num1

num2

```

* Operadores aritméticos

```{r}
num1 <- 10
num2 <- 20
```

```{r}
num1+num2 # Suma
```

```{r}
num2/num1 # División
```

```{r}
num2%%num1 # Resto de división 
```

```{r}
num2^3
```

```{r}
num3 = num1*num2+num1^2 # Tambien se puede utilizar <- 
num3
```
```{r}
peso <- 90 # Peso en Kg
altura <- 1.76 # Altura en metros
IMC <- peso/((altura^2))
IMC
```

* Operadores relacionales

```{r}
num1 == num2 # Comprobamos si las variables son iguales 
```

```{r}
num1 < num2 # Comprobamos num1 y num2
```

```{r}
num1 != num2 # Comprom si las variables son distintas
```

* Operadores lógicos

```{r}
bool1 <- TRUE
bool2 <- FALSE
!bool1 # Negación
```

```{r}
bool1&bool2 # Y
```

```{r}
bool1|bool2 # O
```

```{r}
# ¿Cuál es la edad máxima de las madres del conjunto de datos?

max(birthwt$age)
```
```{r}
# ¿Cuál es la edad mínima de las madres del conjunto de datos?

min(birthwt$age)
```

```{r}
# ¿Cuál es el rango de edad de las madres?
rango_edad <- max(birthwt$age)-min(birthwt$age)
rango_edad
```

```{r}
#¿Cuánto pesa el recien nacido cuya madre tenía la edad máxima?

birthwt$bwt[birthwt$age==max(birthwt$age)]
```

```{r}
# ¿Fumaba la madre cuyo recién nacido era el de menor peso?

birthwt$smoke[birthwt$bwt==min(birthwt$bwt)]
```
```{r}
# Listar los pesos de los recien nacidos, cuyas madres visitaron meno de dos veces al médico durante el primer semestre

birthwt$btw[birthwt$ftv<=2]
```

## **Ejericcio 7**

```{r}
dif_peso <- c(anorexia$Postwt - anorexia$Prewt)
dif_peso
```

```{r}
max(dif_peso)
```

```{r}
anorexia$Treat[dif_peso == max(dif_peso)]
```

```{r}
anorexia$Treat[dif_peso == min(dif_peso)]
```

## Estructuras de datos en R

* Vectores

```{r}
num = c(2, 3, 5, 7, 8) # Crear un vectro numérico
car = c("aa", "bb", "cc") # Crear un vector de tipo cadena de caracteres 

# Combinar vectores

c(num, car)
```

* Crear un vector con valores comprendidos entre 1 y 20 de 2 en 2

```{r}
seq(1, 20, by = 2) 
```

* Crear un vector de 5 elementos que sean todos 1

```{r}
rep(1, 5) 
```

* Tomar el vector de cadena de caracteres del ejemplo anterior
```{r}
car = c("aa", "bb", "cc") 
substr(car, 1, 1) # Muestra el primer carácter de los elementos del vector 
```

```{r}
edad_madres <- c(birthwt$age)
edad_madres
```

## **Ejercicio 8**

```{r}
peso_ganado <- c(anorexia$Postwt - anorexia$Prewt)
peso_ganado
```

* Matrices

```{r}
A = matrix(c(2,3))
B = matrix(c(2,3,4,8,5,6), nrow = 3, ncol = 2)
```

```{r}
A
```

```{r}
B
```

* Combinar matrices

```{r}
B = matrix(c(2,3,4,8,5,6), nrow = 3, ncol = 2)
C = matrix(c(7,4,2), nrow = 3, ncol = 1)
cbind(C, B)
```

```{r}
rbind(C, A) # Combina filas
```

```{r}
c(A) # Convierte una matriz en vector

```

## **Ejercicio 9**

```{r´}
anorexia
```

```{r}
matriz = matrix(c(anorexia$Prewt, anorexia$Postwt), nrow = 72, ncol = 2)
head(matriz)
```

```{r}
# Data frames

attach(birthwt) # fija los datos del data frame birthwt

df_smoke <- subset(birthwt, birthwt$smoke == 1) # Crea un nuevo conjunto de datos con los datos de smoke = 1

```

```{r}
head(df_smoke)
```

```{r}
df_age <- subset(birthwt,birthwt$age < 25)
head(df_age)
```

```{r}
total <- merge(df_smoke, df_age, by = "race") # unimos las dos tablas por el común "race"
head(total)
```

## **Ejercicio 10** 

```{r}
attach(anorexia)
```

```{r}
post_pre_v <- c(anorexia$Postwt - anorexia$Prewt)
post_pre_v
```

```{r}
anorexia_treat_df <- data.frame(anorexia, post_pre_v)
head(anorexia_treat_df)
```

```{r}
anorexia_treat_C_df <- subset(anorexia_treat_df, anorexia_treat_df$Treat == "Cont")
head(anorexia_treat_C_df)
```

```{r}
## Listas 

num <- c(10,20)
car <- c("aa","bb","cc")
```

```{r}
obj.list <- list(num, car) # Crear una lista de un vector numérico y de otro de tipo caracter
obj.list
```

```{r}
obj.list[[1]] # Muestra el primer elemento de la lista definida
```

### Ejercicio 11 

```{r}
anorexia_treat_list <- list(anorexia$Treat, anorexia$Prewt)
anorexia_treat_list
```

```{r}
anorexia_treat_list[[2]]
```
