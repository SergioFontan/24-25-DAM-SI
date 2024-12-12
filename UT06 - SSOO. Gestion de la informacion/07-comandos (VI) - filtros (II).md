
# Filtros en Shell Scripts: Detalles y Ejemplos (Parte 2)

Continuamos con los filtros restantes, explicando su sintaxis, argumentos y ejemplos detallados con salida esperada.

---

## **6. uniq**
**Descripción:** Elimina líneas duplicadas consecutivas en un archivo.

### Sintaxis
```
uniq [opciones] archivo
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-c`          | Muestra un conteo de las repeticiones junto con las líneas únicas. | `uniq -c archivo.txt`                        | Cantidad de repeticiones y líneas únicas.|
| `-d`          | Muestra solo las líneas duplicadas.                    | `uniq -d archivo.txt`                        | Solo las líneas repetidas.          |

---

### Ejemplo con salida:
**Comando:**
```
uniq -c archivo.txt
```
**Explicación:** Muestra el conteo de ocurrencias de cada línea consecutiva en el archivo.
**Salida:**
```
3 Línea repetida
1 Línea única
```

---

## **7. tr**
**Descripción:** Transforma o elimina caracteres en una cadena o archivo.

### Sintaxis
```
tr [opciones] conjunto1 [conjunto2]
```

### Argumentos y Ejemplos

| **Argumento** | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `-d`          | Elimina los caracteres especificados en `conjunto1`.   | `echo "abc123" | tr -d "123"`                  | `abc`                               |
| `-s`          | Suprime caracteres repetidos consecutivos.             | `echo "aaabbcc" | tr -s "a"`                   | `abcc`                              |
| `-c`          | Complementa el conjunto de caracteres especificado.    | `echo "abc123" | tr -c "a-z" "X"`              | `abcXXX`                            |
| `-t`          | Corta el conjunto de salida para que coincida con el tamaño de entrada. | `echo "abc123" | tr "a-z" "A-Z"` | `ABC123`                            |

---

### Ejemplo con salida:
**Comando:**
```
echo "aaabbcc" | tr -s "a"
```
**Explicación:** Suprime repeticiones consecutivas de la letra `a`.
**Salida:**
```
abcc
```

---

## **8. find**
**Descripción:** Busca archivos o directorios según criterios específicos.

### Sintaxis
```
find [ruta] [opciones] [criterios]
```

### Argumentos y Ejemplos

| **Argumento**      | **Descripción**                                        | **Ejemplo**                                  | **Salida esperada**                 |
|---------------------|--------------------------------------------------------|----------------------------------------------|--------------------------------------|
| `+N`               | Coincide con valores mayores que `N`.                  | `find . -size +1M`                           | Archivos mayores de 1 MB.           |
| `-N`               | Coincide con valores menores que `N`.                  | `find . -size -1M`                           | Archivos menores de 1 MB.           |
| `N`                | Coincide con valores exactos.                          | `find . -size 10k`                           | Archivos de exactamente 10 KB.      |
| `-name PATRON`     | Busca archivos que coincidan con el patrón (sensible a mayúsculas). | `find . -name "*.txt"`              | Archivos `.txt`.                    |
| `-iname PATRON`    | Igual que `-name`, pero insensible a mayúsculas.        | `find . -iname "*.txt"`                      | Archivos `.txt` (mayúsculas o minúsculas).|
| `-type [dflbc]`    | Filtra por tipo: `d` directorio, `f` archivo, etc.      | `find . -type f`                             | Solo archivos.                      |
| `-size N[bckwMG]`  | Filtra por tamaño (bloques, KB, MB, etc.).              | `find . -size +1M`                           | Archivos mayores de 1 MB.           |
| `-empty`           | Coincide con archivos o directorios vacíos.            | `find . -empty`                              | Archivos vacíos.                    |
| `-user UNAME`      | Busca archivos de un usuario específico.               | `find . -user usuario`                       | Archivos pertenecientes a `usuario`.|
| `-maxdepth N`      | Limita la profundidad de la búsqueda.                   | `find . -maxdepth 2`                         | Resultados en máximo 2 niveles de profundidad.|

---

### Ejemplo con salida:
**Comando:**
```
find . -name "*.sh"
```
**Explicación:** Busca archivos con extensión `.sh` en el directorio actual y sus subdirectorios.
**Salida:**
```
./script1.sh
./carpeta/script2.sh
```


