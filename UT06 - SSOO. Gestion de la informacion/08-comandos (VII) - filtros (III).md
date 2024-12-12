
# Filtros en Shell Scripts: Detalles y Ejemplos (Parte 3)

Continuamos con los filtros restantes, explicando su sintaxis, argumentos y ejemplos detallados con salida esperada.

---

## **9. grep**
**Descripción:** Busca texto en archivos o entrada estándar que coincida con un patrón.

### Sintaxis
```
grep [opciones] patrón archivo
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-c`          | Muestra solo el número de líneas que coinciden.         | `grep -c "error" archivo.log`                | Número total de coincidencias.      |
| `-i`          | Ignora mayúsculas y minúsculas al buscar.               | `grep -i "error" archivo.log`                | Coincidencias insensibles a caso.   |
| `-l`          | Muestra solo los nombres de los archivos que coinciden.| `grep -l "error" *.log`                      | Lista de archivos que contienen el patrón. |
| `-n`          | Muestra el número de línea junto con la coincidencia.  | `grep -n "error" archivo.log`                | Número de línea y coincidencia.     |
| `-v`          | Muestra líneas que **no** coinciden con el patrón.      | `grep -v "error" archivo.log`                | Líneas que no contienen `error`.    |
| `-r`          | Busca recursivamente en directorios.                   | `grep -r "error" /ruta`                      | Coincidencias en archivos de subdirectorios. |
| `-E`          | Usa expresiones regulares extendidas (ERE).            | `grep -E "error|warning" archivo.log`        | Coincidencias de `error` o `warning`. |
| `-F`          | Interpreta el patrón literalmente (no como una ER).    | `grep -F "error" archivo.log`                | Coincidencias exactas de `error`.   |

---

### Ejemplo con salida:
**Comando:**
```
grep -n "error" archivo.log
```
**Explicación:** Busca la palabra `error` en el archivo y muestra los números de línea.
**Salida:**
```
3:error en la conexión
7:error en el sistema
```

---

## **10. fgrep**
**Descripción:** Busca texto en archivos, pero trata el patrón literalmente (sin interpretarlo como una expresión regular).

### Sintaxis
```
fgrep [opciones] patrón archivo
```

---

### Ejemplo con salida:
**Comando:**
```
fgrep "[error]" archivo.log
```
**Explicación:** Busca literalmente la cadena `[error]` en el archivo.
**Salida:**
```
[error] encontrado
```

---

## **11. egrep**
**Descripción:** Busca texto en archivos usando expresiones regulares extendidas (ERE).

### Sintaxis
```
egrep [opciones] patrón archivo
```

---

### Ejemplo con salida:
**Comando:**
```
egrep "error|warning" archivo.log
```
**Explicación:** Busca líneas que contengan `error` o `warning` en el archivo.
**Salida:**
```
error en la conexión
warning: disco lleno
```

---

## **12. sed**
**Descripción:** Editor de flujo que procesa y transforma texto en línea.

### Sintaxis
```
sed [opciones] 'instrucción' archivo
```

### Instrucciones básicas

| **Instrucción** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|-----------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `i`            | Inserta texto antes de una línea específica.            | `sed '2i\Nueva línea' archivo.txt`         | Nueva línea añadida antes de la línea 2. |
| `a`            | Añade texto después de una línea específica.            | `sed '3a\Texto adicional' archivo.txt`     | Línea añadida después de la línea 3. |
| `c`            | Cambia el contenido de una línea.                       | `sed '2c\Texto cambiado' archivo.txt`      | Línea 2 reemplazada por `Texto cambiado`. |
| `d`            | Elimina líneas específicas.                             | `sed '3d' archivo.txt`                      | Línea 3 eliminada.                   |
| `p`            | Imprime líneas que coinciden con el patrón.             | `sed -n '/error/p' archivo.log`             | Solo se imprimen las líneas con `error`. |
| `s`            | Sustituye texto que coincide con un patrón.             | `sed 's/error/solución/g' archivo.txt`      | Reemplaza todas las ocurrencias de `error` por `solución`. |
| `!`            | Aplica la instrucción a las líneas que **no** coinciden.| `sed '/error/!d' archivo.log`               | Solo muestra líneas que **no** contengan `error`. |

---

### Ejemplo con salida:
**Comando:**
```
sed 's/error/solución/g' archivo.log
```
**Explicación:** Reemplaza todas las ocurrencias de `error` por `solución`.
**Salida:**
```
solución en la conexión
solución en el sistema
```

---
