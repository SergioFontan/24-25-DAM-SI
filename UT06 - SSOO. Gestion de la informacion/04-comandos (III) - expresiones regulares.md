
# Expresiones Regulares Básicas (ER) en Shell Scripts

## ¿Qué son las expresiones regulares?

Las expresiones regulares (ER) son patrones que definen un conjunto de cadenas de caracteres. Estas se utilizan para buscar, manipular y procesar texto en herramientas como `grep`, `sed` o `awk`. Una expresión regular puede combinar caracteres normales y metacaracteres para crear patrones específicos.

---

## Usos frecuentes de las expresiones regulares

1. **Búsqueda de texto:** Encontrar líneas específicas en un archivo o resultados de comandos.
2. **Validación de datos:** Verificar que el texto cumple con un formato (por ejemplo, correos electrónicos).
3. **Filtrado:** Procesar y reducir resultados de comandos para mostrar solo lo relevante.
4. **Edición masiva:** Modificar texto en múltiples líneas o archivos.

---

## Tipos de expresiones regulares

### Básicas (ER - Basic Regular Expressions)
Son el tipo más sencillo y son compatibles con herramientas como `grep` y `sed` por defecto.

- Caracteres normales: Representan directamente lo que se busca.
- Metacaracteres: Introducen patrones más complejos (como `^` o `$`).

---

## 1. Metacaracteres básicos 

| **ER** | **Descripción**                                                                 | **Ejemplo**                                                                                                                                     |
|--------|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| `.`    | Coincide con cualquier carácter.                                               | `echo "abc" | grep "a.c"`  → Salida: `abc`                                                                                                                 |
| `[ ]`  | Coincide con cualquiera de los caracteres especificados entre corchetes.       | `echo "a b c" | grep "[abc]"`  → Salida: `a`, `b`, `c`                                                                                                         |
| `[^ ]` | Coincide con cualquier carácter que NO esté entre los corchetes.               | `echo "abc" | grep "[^b]"`  → Salida: `a`, `c`                                                                                                               |
| `^`    | Coincide con el inicio de una línea.                                           | `echo -e "linea1\nlinea2" | grep "^linea1"`  → Salida: `linea1`                                                                                                             |
| `$`    | Coincide con el final de una línea.                                            | `echo -e "linea1\nlinea2" | grep "linea2$"`  → Salida: `linea2`                                                                                                             |
| `*`    | Coincide con 0 o más ocurrencias del carácter o patrón anterior.               | `echo "aaaa" | grep "a*"`  → Salida: `aaaa`                                                                                                                   |
| `\`   | Escapa un metacaracter para tratarlo como carácter literal.                    | `echo "*special" | grep "\\*"`  → Salida: `*special`                                                                                                             |

---

## Ejemplos detallados

### Uso de `.`
**Comando:**
```
echo "abc" | grep "a.c"
```
**Explicación:** El patrón `a.c` busca cualquier cadena donde `a` esté seguido de un carácter cualquiera (`.`) y luego `c`.
**Salida:**
```
abc
```

---

### Uso de `[ ]`
**Comando:**
```
echo "apple banana cherry" | grep "[ab]"
```
**Explicación:** El patrón `[ab]` coincide con cualquier línea que contenga los caracteres `a` o `b`.
**Salida:**
```
apple
banana
```

---

### Uso de `[^ ]`
**Comando:**
```
echo "apple banana cherry" | grep "[^ab]"
```
**Explicación:** El patrón `[^ab]` coincide con cualquier línea que NO contenga `a` ni `b`.
**Salida:**
```
cherry
```

---

### Uso de `^`
**Comando:**
```
echo -e "start
middle
end" | grep "^start"
```
**Explicación:** El patrón `^start` busca líneas que comiencen con `start`.
**Salida:**
```
start
```

---

### Uso de `$`
**Comando:**
```
echo -e "start
middle
end" | grep "end$"
```
**Explicación:** El patrón `end$` busca líneas que terminen con `end`.
**Salida:**
```
end
```

---

### Uso de `*`
**Comando:**
```
echo "aaaa bbbb cccc" | grep "a*"
```
**Explicación:** El patrón `a*` busca 0 o más ocurrencias consecutivas de `a`.
**Salida:**
```
aaaa
```

---

### Uso de `\`
**Comando:**
```
echo "*special" | grep "\*"
```
**Explicación:** El patrón `\*` escapa el carácter `*` para tratarlo como literal.
**Salida:**
```
*special
```

---

### Extendidas (ERE)
Las expresiones regulares extendidas (ERE) son una ampliación de las expresiones regulares básicas (ER) que permiten trabajar con patrones más complejos y precisos. 

Las ERE se caracterizan por incluir metacaracteres adicionales y simplificar ciertas construcciones de patrones que, en las ER básicas, requerirían escape o combinaciones más complicadas.

En esencia, las ERE son un conjunto más amplio de herramientas para definir patrones que permiten:

- **Especificar repeticiones**: Como una o más (+), cero o una (?), o rangos ({n,m}).
- **Utilizar alternancia**: Con el operador | para definir opciones posibles en un patrón.
- **Simplificar agrupaciones**: Mediante paréntesis () sin necesidad de escapes adicionales.

### 2. Metacaracteres extendidos

| **ERE**   | **Descripción** | **Ejemplo** | **Salida esperada** |
|-----------|-----------------|-------------|---------------------|
| `+`       | Una o más ocurrencias del carácter anterior. | `echo "abbc" | egrep "ab+c"` | `abbc` |
| `?`       | Cero o una ocurrencia del carácter anterior. | `echo "abc ac" | egrep "ab?c"` | `abc`, `ac` |
| `{n}`     | Exactamente n ocurrencias del carácter anterior. | `echo "aaa" | egrep "a{3}"` | `aaa` |
| `{n,}`    | Al menos n ocurrencias del carácter anterior. | `echo "aaaa" | egrep "a{3,}"` | `aaaa` |
| `{n,m}`   | Entre n y m ocurrencias del carácter anterior. | `echo "aaa" | egrep "a{2,3}"` | `aa`, `aaa` |
| `(a|b)`   | Alternancia: coincide con `a` o `b`. | `echo "apple banana" | egrep "(apple|banana)"` | `apple`, `banana` |

---

### 3. Alternancia

| **ER**      | **Descripción**             | **Ejemplo**                                    | **Salida esperada** |
| ----------- | --------------------------- | ---------------------------------------------- | ------------------- |
| `(a|b)`     | Coincide con `a` o `b`.     | `echo "apple banana" | egrep "(apple|banana)"` | `apple`, `banana`   |
| `(abc|xyz)` | Coincide con `abc` o `xyz`. | `echo "abc xyz" | egrep "(abc|xyz)"`           | `abc`, `xyz`        |

### 4. Clases de caracteres

### 

| **Clase**   | **Descripción**                               | **Ejemplo**                            | **Salida esperada**          |
| ----------- | --------------------------------------------- | -------------------------------------- | ---------------------------- |
| `[:digit:]` | Coincide con cualquier dígito.                | `echo "123 abc" | egrep "[[:digit:]]"` | `1`, `2`, `3`                |
| `[:alpha:]` | Coincide con cualquier carácter alfabético.   | `echo "abc ABC" | egrep "[[:alpha:]]"` | `a`, `b`, `c`, `A`, `B`, `C` |
| `[:alnum:]` | Coincide con caracteres alfanuméricos.        | `echo "a1b2" | egrep "[[:alnum:]]"`    | `a`, `1`, `b`, `2`           |
| `[:upper:]` | Coincide con letras mayúsculas.               | `echo "ABC abc" | egrep "[[:upper:]]"` | `A`, `B`, `C`                |
| `[:lower:]` | Coincide con letras minúsculas.               | `echo "ABC abc" | egrep "[[:lower:]]"` | `a`, `b`, `c`                |
| `[:space:]` | Coincide con espacios, tabulaciones y saltos. | `echo "a b\tc" | egrep "[[:space:]]"`  | ` `, `\t`                    |
| `[:punct:]` | Coincide con signos de puntuación.            | `echo "! @ #" | egrep "[[:punct:]]"`   | `!`, `@`, `#`                |

---

## Ejemplos combinados

### Ejemplo 1: Alternancia y repetición
**Comando:**
```
echo "apple banana cherry" | egrep "(apple|banana){1,2}"
```
**Explicación:** Busca cadenas donde `apple` o `banana` aparezcan 1 o 2 veces consecutivas.
**Salida:**
```
apple
banana
```

### Ejemplo 2: Uso de clases de caracteres
**Comando:**
```
echo "abc 123 !" | egrep "[[:alpha:][:digit:]]"
```
**Explicación:** Coincide con caracteres alfanuméricos (letras o números).
**Salida:**
```
a
b
c
1
2
3
```

### Ejemplo 3: Alternancia con grupos

**Comando:**

```
echo "cat dog bird" | egrep "(cat|dog)"
```

**Explicación:** Coincide con cadenas que contienen `cat` o `dog`.
**Salida:**

```
cat
dog
```

---

### Ejemplo 4: Clases de caracteres con `[:digit:]`

**Comando:**

```
echo "abc 123 xyz" | egrep "[[:digit:]]"
```

**Explicación:** Coincide con cualquier dígito presente en la cadena.
**Salida:**

```
1
2
3
```

---

### Ejemplo 5: Combinación de metacaracteres

**Comando:**

```
echo "a1b2c3" | egrep "a[[:digit:]]b"
```

**Explicación:** Coincide con cadenas donde `a` es seguido por un dígito y luego por `b`.
**Salida:**

```
a1b
```

---

