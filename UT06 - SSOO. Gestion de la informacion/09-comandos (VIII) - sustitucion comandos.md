
# Sustitución de Comandos en Shell Scripts

## ¿Qué es la sustitución de comandos?

La **sustitución de comandos** permite utilizar la salida de un comando como entrada en otro lugar del script. Esto se logra ejecutando el comando dentro de una construcción especial, y el resultado se reemplaza en el lugar donde aparece.

---

## Sintaxis de la sustitución de comandos

Existen dos formas principales para realizar la sustitución de comandos:

1. **Usando `$()`**
   - Es la forma moderna y recomendada debido a su claridad y compatibilidad.
   - Ejemplo de sintaxis:
     ```
     $(comando)
     ```

2. **Usando comillas invertidas: `` `comando` ``**
   - Es una forma más antigua, pero aún soportada en la mayoría de los shells.
   - Ejemplo de sintaxis:
     ```
     `comando`
     ```

---

## Ejemplo con `$()`

**Código:**
```bash
if [ $(id -u alfonso) -ge 1000 ]
then
    echo "El UID del usuario alfonso es mayor o igual a 1000"
else
    echo "El UID del usuario alfonso es menor a 1000"
fi
```

**Explicación:**
- `id -u alfonso`: Obtiene el UID del usuario `alfonso`.
- `$(id -u alfonso)`: Sustituye la salida del comando `id -u alfonso` en la condición del `if`.
- El script evalúa si el UID del usuario es mayor o igual a 1000 y realiza una acción dependiendo del resultado.

**Salida esperada:**
```
El UID del usuario alfonso es mayor o igual a 1000
```

---

## Ejemplo con comillas invertidas

**Código:**
```bash
if [ `id -u alfonso` -ge 1000 ]
then
    echo "El UID del usuario alfonso es mayor o igual a 1000"
else
    echo "El UID del usuario alfonso es menor a 1000"
fi
```

**Explicación:**
- Similar al caso anterior, pero utiliza comillas invertidas para realizar la sustitución de comandos.

**Salida esperada:**
```
El UID del usuario alfonso es mayor o igual a 1000
```

---

## Ventajas de `$()` frente a `` ` ``

1. **Legibilidad:**
   - `$()` es más claro y fácil de leer en comparación con las comillas invertidas.

2. **Anidación:**
   - Es más sencillo anidar sustituciones con `$()`:
     ```bash
     echo $(ls $(dirname /ruta/archivo))
     ```
   - Con comillas invertidas, sería más difícil de leer:
     ```bash
     echo `ls \`dirname /ruta/archivo\``
     ```

3. **Compatibilidad:**
   - Aunque ambas formas son compatibles con la mayoría de los shells, `$()` es más estándar en los scripts modernos.

---

## Usos frecuentes de la sustitución de comandos

1. **Asignación de variables:**
   ```bash
   resultado=$(ls -l /directorio)
   ```

2. **Condiciones en estructuras de control:**
   ```bash
   if [ $(wc -l < archivo.txt) -gt 10 ]
   then
       echo "El archivo tiene más de 10 líneas"
   fi
   ```

3. **Combinación con otros comandos:**
   ```bash
   echo "Hoy es $(date)"
   ```

---

## Consideraciones importantes

- **Escape de caracteres:** En algunos casos, es necesario escapar caracteres especiales dentro de las comillas invertidas.
- **Compatibilidad:** Aunque las comillas invertidas son compatibles, se recomienda utilizar `$()` para scripts más modernos y mantenibles.

---

Este documento explica la sustitución de comandos en shell scripts, destacando sus sintaxis, usos y ventajas con ejemplos prácticos.
