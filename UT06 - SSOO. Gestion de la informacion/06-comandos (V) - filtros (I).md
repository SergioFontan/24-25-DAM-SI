
# Filtros en Shell Scripts: Detalles y Ejemplos

Este documento describe los filtros solicitados, su sintaxis, argumentos, y ejemplos detallados, mostrando también la salida esperada en la terminal.

---

## **1. head**
**Descripción:** Muestra las primeras líneas de un archivo.

### Sintaxis
```
head [opciones] archivo
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                      | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-N`          | Muestra las primeras N líneas del archivo.           | `head -5 archivo.txt`                        | Las primeras 5 líneas del archivo.  |
| `-n N`        | Igual que `-N`, muestra las primeras N líneas.       | `head -n 3 archivo.txt`                      | Las primeras 3 líneas del archivo.  |
| `-c N`        | Muestra los primeros N bytes del archivo.            | `head -c 10 archivo.txt`                     | Los primeros 10 caracteres del archivo. |

---

### Ejemplo con salida:
**Comando:**
```
head -3 archivo.txt
```
**Explicación:** Muestra las primeras 3 líneas del archivo.
**Salida:**
```
Línea 1
Línea 2
Línea 3
```

---

## **2. tail**
**Descripción:** Muestra las últimas líneas de un archivo.

### Sintaxis
```
tail [opciones] archivo
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-N`          | Muestra las últimas N líneas del archivo.              | `tail -5 archivo.txt`                        | Las últimas 5 líneas del archivo.   |
| `-n N`        | Igual que `-N`, muestra las últimas N líneas.          | `tail -n 3 archivo.txt`                      | Las últimas 3 líneas del archivo.   |
| `-n +N`       | Muestra el archivo comenzando desde la línea N.        | `tail -n +2 archivo.txt`                     | Desde la segunda línea en adelante. |
| `-c N`        | Muestra los últimos N bytes del archivo.               | `tail -c 15 archivo.txt`                     | Los últimos 15 caracteres del archivo.|

---

### Ejemplo con salida:
**Comando:**
```
tail -n +3 archivo.txt
```
**Explicación:** Muestra el archivo desde la tercera línea en adelante.
**Salida:**
```
Línea 3
Línea 4
Línea 5
```

---

## **3. wc**
**Descripción:** Cuenta líneas, palabras, caracteres o bytes de un archivo.

### Sintaxis
```
wc [opciones] archivo
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-l`          | Muestra solo el número de líneas.                      | `wc -l archivo.txt`                          | Número total de líneas.             |
| `-w`          | Muestra solo el número de palabras.                    | `wc -w archivo.txt`                          | Número total de palabras.           |
| `-c`          | Muestra solo el tamaño en bytes.                       | `wc -c archivo.txt`                          | Número total de bytes.              |
| `-m`          | Muestra solo el número de caracteres.                  | `wc -m archivo.txt`                          | Número total de caracteres.         |
| `-L`          | Muestra la longitud de la línea más larga.             | `wc -L archivo.txt`                          | Longitud de la línea más larga.     |

---

### Ejemplo con salida:
**Comando:**
```
wc -w archivo.txt
```
**Explicación:** Cuenta las palabras en el archivo.
**Salida:**
```
42 archivo.txt
```

---

## **4. cut**
**Descripción:** Extrae columnas o segmentos específicos de texto.

### Sintaxis
```
cut [opciones] archivo
```

### Intervalos admitidos
1. `N`: Extrae solo el N-ésimo elemento.
2. `N-`: Extrae desde el elemento N hasta el final.
3. `N-M`: Extrae desde el elemento N hasta el M.
4. `-M`: Extrae desde el inicio hasta el elemento M.

---

### Argumentos y Ejemplos

| **Argumento**      | **Descripción**                                      | **Ejemplo**                                  | **Salida esperada**                 |
|--------------------|------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-b intervalo`     | Extrae bytes en el intervalo especificado.           | `cut -b 1-5 archivo.txt`                     | Los primeros 5 bytes de cada línea. |
| `-c intervalo`     | Extrae caracteres en el intervalo especificado.      | `cut -c 3-8 archivo.txt`                     | Caracteres 3 al 8 de cada línea.    |
| `-d DELIM`         | Especifica un delimitador para dividir columnas.     | `cut -d "," -f 2 archivo.csv`                | Segunda columna usando `,` como delimitador.|
| `-f intervalo`     | Extrae campos en el intervalo especificado.          | `cut -d "," -f 1-3 archivo.csv`              | Las primeras 3 columnas del archivo.|

---

### Ejemplo con salida:
**Comando:**
```
cut -d "," -f 2 archivo.csv
```
**Explicación:** Extrae la segunda columna del archivo CSV.
**Salida:**
```
Columna2
Valor2
Dato2
```

---

## **5. sort**
**Descripción:** Ordena líneas de texto de un archivo.

### Sintaxis
```
sort [opciones] archivo
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-t SEP`      | Define el separador de columnas.                       | `sort -t "," -k 2 archivo.csv`               | Ordena por la segunda columna del CSV.|
| `-n`          | Ordena numéricamente.                                  | `sort -n archivo.txt`                        | Orden numérico.                     |
| `-r`          | Ordena en orden inverso.                               | `sort -r archivo.txt`                        | Orden descendente.                  |
| `-k numero`   | Ordena según la columna especificada.                  | `sort -k 3 archivo.txt`                      | Ordena por la tercera columna.      |
| `-u`          | Elimina duplicados mientras ordena.                    | `sort -u archivo.txt`                        | Sin duplicados.                     |
| `-f`          | Ignora mayúsculas y minúsculas al ordenar.             | `sort -f archivo.txt`                        | Orden insensible a mayúsculas.      |

---

### Ejemplo con salida:
**Comando:**
```
sort -t "," -k 2 archivo.csv
```
**Explicación:** Ordena el archivo CSV por la segunda columna.
**Salida:**
```
Valor1,Columna2,Dato3
Valor2,Columna1,Dato2
```

---


