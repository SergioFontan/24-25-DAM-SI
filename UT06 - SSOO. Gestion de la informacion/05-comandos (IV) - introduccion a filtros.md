
# Filtros en Shell Scripts

## ¿Qué son los filtros?

En el contexto de los shell scripts, los filtros son comandos que procesan datos, generalmente texto, para transformarlos, manipularlos o analizarlos. 
Los filtros toman una entrada (input), la procesan según ciertas reglas o patrones y devuelven una salida (output). 
Esta salida puede ser utilizada directamente en la terminal, almacenada en un archivo o pasada como entrada a otro comando mediante una tubería (`|`).

---

## Características de los filtros

1. **Procesan texto línea por línea:**
   - La mayoría de los filtros operan línea por línea, haciendo que sean muy eficientes para manipular grandes cantidades de datos.

2. **Entrada y salida estándar:**
   - Reciben la entrada estándar (stdin), que puede venir de un archivo o de la salida de otro comando.
   - Devuelven la salida estándar (stdout), que puede mostrarse en la terminal o redirigirse a otro comando o archivo.

3. **Combinación con tuberías (`|`):**
   - Los filtros se utilizan comúnmente en cadenas de comandos, donde la salida de un filtro es la entrada de otro.

4. **Flexible y reutilizable:**
   - Los filtros pueden ser combinados en diferentes órdenes para realizar tareas complejas.

---

## ¿Para qué se usan los filtros?

1. **Buscar y extraer información:**
   - Localizar líneas que coincidan con ciertos patrones o palabras clave.
   - Extraer columnas específicas de datos.

2. **Ordenar y organizar datos:**
   - Clasificar líneas alfabética o numéricamente.
   - Eliminar duplicados o líneas redundantes.

3. **Transformar datos:**
   - Convertir texto en mayúsculas/minúsculas.
   - Sustituir palabras o caracteres.

4. **Estadísticas simples:**
   - Contar líneas, palabras, o caracteres.
   - Calcular totales o promedios.

5. **Manipulación de archivos:**
   - Dividir archivos en partes más pequeñas.
   - Mostrar secciones específicas de un archivo.

---

## Usos frecuentes de los filtros

1. **Analizar logs y reportes:**
   - Procesar registros del sistema para encontrar errores, patrones o tendencias.
   - Extraer información útil de archivos grandes.

2. **Procesamiento de datos:**
   - Manipular datos en formato tabular o estructurado.
   - Preparar datos para scripts o programas.

3. **Automatización:**
   - Realizar tareas repetitivas o rutinarias mediante scripts que usen filtros.

4. **Filtrado de resultados:**
   - Reducir la salida de un comando a solo lo necesario.

---

## Ejemplos básicos del flujo de filtros

### Ejemplo 1: Búsqueda de texto
**Comando:**
```
grep "error" archivo.log
```
**Explicación:** Busca líneas que contengan la palabra `error` en el archivo `archivo.log` y las muestra.

---

### Ejemplo 2: Contar líneas
**Comando:**
```
wc -l archivo.txt
```
**Explicación:** Cuenta el número de líneas en el archivo `archivo.txt`.

---

### Ejemplo 3: Ordenar datos
**Comando:**
```
sort archivo.txt
```
**Explicación:** Ordena las líneas del archivo `archivo.txt` en orden alfabético.

---

### Ejemplo 4: Encadenar filtros
**Comando:**
```
cat archivo.txt | grep "pattern" | sort | uniq
```
**Explicación:** Combina varios filtros para:
1. Mostrar el contenido del archivo con `cat`.
2. Filtrar las líneas que coincidan con `pattern` usando `grep`.
3. Ordenar las líneas con `sort`.
4. Eliminar duplicados con `uniq`.

---

### Ejemplo 5: Manipulación de texto
**Comando:**
```
tr 'a-z' 'A-Z' < archivo.txt
```
**Explicación:** Convierte todo el texto en el archivo `archivo.txt` de minúsculas a mayúsculas.

---

## Ventajas de los filtros

1. **Eficiencia:** Operan directamente en la entrada y la salida estándar, evitando la creación de archivos temporales innecesarios.
2. **Simplicidad:** Su sintaxis y funcionalidad son directas, lo que los hace fáciles de aprender y utilizar.
3. **Flexibilidad:** Pueden combinarse para realizar tareas complejas con unos pocos comandos.
4. **Portabilidad:** Funcionan en cualquier sistema operativo basado en Unix/Linux.

---

