
# Gestión de Ficheros y Directorios en Ubuntu: Comandos Clave

En esta sección aprenderás sobre los comandos más comunes para gestionar ficheros y directorios en Ubuntu. Cada comando incluye una explicación, su sintaxis, una tabla de argumentos y ejemplos detallados con simulación de la terminal.

---

## 1. `ls`
- **Descripción:** Lista los contenidos de un directorio.
- **Sintaxis:** 
  ```
  ls [opciones] [directorio]
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-l`       | Lista en formato detallado (permisos, tamaño, etc.).      |
| `-a`       | Incluye archivos ocultos.                                 |
| `-s`       | Muestra el tamaño de cada archivo en bloques.             |
| `-R`       | Lista recursivamente el contenido de subdirectorios.      |
| `-t`       | Ordena por fecha de modificación (más reciente primero).  |
| `-S`       | Ordena por tamaño (de mayor a menor).                     |
| `-h`       | Tamaño de archivos legible por humanos. |

### Ejemplos:
**Comando:**
```
ls -l -a
```
**Salida:**
```
drwxr-xr-x  2 usuario usuario 4096 dic 11 08:00 .
drwxr-xr-x  5 usuario usuario 4096 dic 11 07:00 ..
-rw-r--r--  1 usuario usuario 1024 dic 10 22:00 archivo.txt
```

**Comando combinado:**
```
ls -lh -S
```
**Salida:**
```
-rw-r--r--  1 usuario usuario 1.1M dic 10 22:00 grande.txt
-rw-r--r--  1 usuario usuario 120K dic 10 20:00 medio.txt
```

---

## 2. `cp`
- **Descripción:** Copia archivos o directorios.
- **Sintaxis:** 
  ```
  cp [opciones] origen destino
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-p`       | Conserva los permisos y marcas de tiempo originales.      |
| `-i`       | Solicita confirmación antes de sobrescribir archivos.     |
| `-R`       | Copia recursivamente directorios y sus contenidos.        |
| `-a`       | Copia archivos con estructura y atributos completos.      |
| `-u`       | Copia solo si el archivo de origen es más reciente.       |
| `-r`       | Copia directorios de forma recursiva. |
| `-v`       | Muestra los detalles de las acciones realizadas. |

### Ejemplo:
**Comando:**
```
cp -a carpeta_origen carpeta_destino
```
**Salida:**
(No hay salida, pero `carpeta_destino` contiene una copia exacta de `carpeta_origen`).

**Comando:**
```
cp -v archivo.txt /destino/
```
**Salida:**
```
'archivo.txt' -> '/destino/archivo.txt'
```

**Comando:**
```
cp -r carpeta_origen carpeta_destino
```
**Salida:**
```
'carpeta_origen' -> 'carpeta_destino'
```

---

## 3. `mv`
- **Descripción:** Mueve o renombra archivos y directorios.
- **Sintaxis:** 
  ```
  mv [opciones] origen destino
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-i`       | Solicita confirmación antes de sobrescribir archivos.     |
| `-v`       | Muestra los detalles de las acciones realizadas. |

### Ejemplo:
**Comando:**
```
mv -i archivo.txt carpeta/
```
**Salida:**
```
mv: sobrescribir 'carpeta/archivo.txt'? y
```
**Comando:**
```
mv -v archivo.txt carpeta/
```
**Salida:**
```
'archivo.txt' -> 'carpeta/archivo.txt'
```
---

## 4. `cd`
- **Descripción:** Cambia el directorio actual.
- **Sintaxis:** 
  ```
  cd [directorio]
  ```

### Ejemplo:
**Comando:**
```
cd /home/usuario
```
**Salida:**
(No se muestra salida, pero el directorio actual cambia a `/home/usuario`).

--- 

## 5. `touch`
- **Descripción:** Crea archivos vacíos o actualiza la fecha de modificación de un archivo.
- **Sintaxis:** 
  ```
  touch [opciones] archivo
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-a`       | Cambia solo la fecha de acceso del archivo.               |
| `-m`       | Cambia solo la fecha de modificación del archivo.         |
| `-d`       | Establece una fecha específica.                           |

### Ejemplo:
**Comando:**
```
touch -d "2024-12-11 12:34" archivo.txt
```
**Salida:**
(No hay salida, pero la fecha de `archivo.txt` se actualiza).

---

## 6. `rm`
- **Descripción:** Elimina archivos o directorios.
- **Sintaxis:** 
  ```
  rm [opciones] archivo/directorio
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-i`       | Solicita confirmación antes de eliminar.                  |
| `-r`       | Elimina directorios de forma recursiva.                   |
| `-f`       | Fuerza la eliminación sin confirmación. |

### Ejemplo:
**Comando combinado:**
```
rm -r -i carpeta/
```
**Salida:**
```
rm: ¿descender en el directorio 'carpeta'? y
```
---

## 7. `rmdir`
- **Descripción:** Elimina directorios vacíos.
- **Sintaxis:** 
  ```
  rmdir directorio
  ```

### Ejemplo:
**Comando:**
```
rmdir carpeta_vacía
```
**Salida:**
(No se muestra salida, pero el directorio `carpeta_vacía` se elimina).

---

## 8. `pwd`
- **Descripción:** Muestra el directorio actual.
- **Sintaxis:** 
  ```
  pwd
  ```

### Ejemplo:
**Comando:**
```
pwd
```
**Salida:**
```
/home/usuario
```
---

## 6. `mkdir`
- **Descripción:** Crea un nuevo directorio.
- **Sintaxis:** 
  ```
  mkdir [opciones] nombre_directorio
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-p`       | Crea directorios de forma recursiva.                      |
| `-m`       | Establece permisos al crear el directorio.                |

### Ejemplo:
**Comando:**
```
mkdir -p padre/hijo
```
**Salida:**
(No hay salida, pero los directorios `padre` y `hijo` se crean).

---

## 10. `whoami`
- **Descripción:** Muestra el nombre del usuario actual.
- **Sintaxis:** 
  ```
  whoami
  ```

### Ejemplo:
**Comando:**
```
whoami
```
**Salida:**
```
usuario
```

---

## 7. `date`
- **Descripción:** Muestra la fecha y hora actual.
- **Sintaxis:** 
  ```
  date [opciones]
  ```
- **Argumentos:**

| **Formato** | **Descripción**                                           |
|-------------|-----------------------------------------------------------|
| `%a`        | Día abreviado (ej: "Lun").                                |
| `%A`        | Día completo (ej: "Lunes").                               |
| `%b`        | Mes abreviado (ej: "Dic").                                |
| `%B`        | Mes completo (ej: "Diciembre").                           |
| `%d`        | Día del mes (01-31).                                      |
| `%y`        | Año en dos dígitos (ej: "24").                            |
| `%m`        | Mes en número (01-12).                                    |
| `%H`        | Hora (00-23).                                             |
| `%M`        | Minuto (00-59).                                           |
| `%S`        | Segundo (00-59).                                          |
| `+%d-%m-%Y`| Formato personalizado para mostrar día, mes y año. |

### Ejemplo:
**Comando combinado:**
```
date +"Hoy es %A, %d de %B de %Y y son las %H:%M:%S"
```
**Salida:**
```
Hoy es Lunes, 11 de Diciembre de 2024 y son las 12:34:56
```
**Comando:**
```
date +%d-%m-%Y
```
**Salida:**
```
11-12-2024
```

---

## 12. `cat`
- **Descripción:** Muestra el contenido de un archivo.
- **Sintaxis:** 
  ```
  cat archivo
  ```

### Ejemplo:
**Comando:**
```
cat archivo.txt
```
**Salida:**
```
Contenido del archivo.
```
---


## 8. `du`
- **Descripción:** Muestra el uso del disco.
- **Sintaxis:** 
  ```
  du [opciones] [directorio/archivo]
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-h`       | Muestra el tamaño en formato legible.                     |
| `-b`       | Muestra el tamaño en bytes.                               |
| `-k`       | Muestra el tamaño en kilobytes.                           |
| `-m`       | Muestra el tamaño en megabytes.                           |
| `-s`       | Muestra el tamaño total resumido.                         |

### Ejemplo:
**Comando combinado:**
```
du -h -s carpeta
```
**Salida:**
```
4.0K  carpeta
```

---

## 9. `df`
- **Descripción:** Muestra información sobre el espacio libre en disco.
- **Sintaxis:** 
  ```
  df [opciones]
  ```
- **Argumentos:**

| **Opción** | **Descripción**                                           |
|------------|-----------------------------------------------------------|
| `-h`       | Muestra el tamaño en formato legible.                     |
| `-k`       | Muestra el tamaño en kilobytes.                           |
| `-m`       | Muestra el tamaño en megabytes.                           |

### Ejemplo:
**Comando combinado:**
```
df -h
```
**Salida:**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   30G   70G  30% /
```

## 15. `file`
- **Descripción:** Identifica el tipo de archivo.
- **Sintaxis:** 
  ```
  file archivo
  ```

### Ejemplo:
**Comando:**
```
file archivo.txt
```
**Salida:**
```
archivo.txt: texto plano
```


---


