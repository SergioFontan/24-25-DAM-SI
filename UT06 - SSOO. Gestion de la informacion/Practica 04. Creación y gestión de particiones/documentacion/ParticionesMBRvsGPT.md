
# Resumen de Particiones Primarias y Extendidas en GPT y MBR

## Comparativa General

| **Aspecto**                     | **MBR (Master Boot Record)**                  | **GPT (GUID Partition Table)**                  |
|----------------------------------|-----------------------------------------------|------------------------------------------------|
| **Límite de particiones primarias** | Máximo 4                                     | Máximo 128 (por defecto, configurable más)      |
| **Partición extendida**          | Necesaria si quieres más de 4 particiones.    | No existe ni es necesaria.                     |
| **Particiones lógicas**          | Se crean dentro de la partición extendida.    | No aplicable.                                  |
| **Gestión de particiones**       | Limitada por el esquema; mezcla primarias y lógicas. | Todas las particiones son tratadas como primarias. |
| **Compatibilidad de partición extendida** | **Sí**, se puede crear para contener lógicas. | **No**, no se puede crear (GPT no las soporta). |
| **Errores al crear extendidas**  | No da error, son parte del diseño.            | Muestra error al intentar crearla, ya que GPT no las soporta. |
| **Aparición en herramientas**    | Listadas como `Extended` y las lógicas tienen numeración separada (por ejemplo, `/dev/sda5`, `/dev/sda6`). | No hay extendidas; todas las particiones aparecen con numeración primaria (por ejemplo, `/dev/sda1`, `/dev/sda2`). |

---

## 1. Particiones en MBR

### Particiones Primarias
- **Límite**: Hasta **4 particiones primarias**.
- Se usan para almacenar directamente datos o instalar sistemas operativos.
- Si necesitas más de 4 particiones, debes usar una partición extendida.

### Particiones Extendidas
- **Límite**: Solo puede haber **1 partición extendida**.
- No almacena datos directamente; actúa como un contenedor para particiones lógicas.
- Las particiones lógicas dentro de la extendida comienzan a numerarse desde `/dev/sda5`.
- Aparecen en herramientas como `fdisk` o `parted`:
  - La extendida será identificada como un contenedor.
  - Las lógicas aparecerán individualmente listadas.

### Errores al Crear Extendidas
- No hay errores al crear extendidas; forman parte del diseño de MBR.

### Ejemplo de salida con `fdisk` en MBR:
```
Device      Boot   Start       End       Blocks    Id  System
/dev/sda1   *      2048       1050623   524288    83  Linux
/dev/sda2          1050624    2097151   524288    83  Linux
/dev/sda3          2097152    976773167 487837008 5   Extended
/dev/sda5          2101248    31457279  14656016  83  Linux
/dev/sda6          31459328   62914559  15728616  83  Linux
```

---

## 2. Particiones en GPT

### Particiones Primarias
- **Límite**: Hasta **128 particiones primarias** por defecto (configurable para más).
- Todas las particiones son tratadas como primarias; no hay distinción entre primarias, extendidas o lógicas.
- No se requiere ninguna estructura adicional para manejar muchas particiones.

### Particiones Extendidas
- **No existen en GPT**. No hay soporte para particiones extendidas ni lógicas.
- Intentar crear una partición extendida dará error.

### Errores al Crear Extendidas
- Al intentar crear una partición extendida en un disco GPT con herramientas modernas, como `fdisk` o `parted`, se genera un error similar a:
  ```
  Partition type 'e' is not supported with GPT.
  ```

### Aparición en Herramientas
- Solo se listan particiones primarias con nombres consecutivos (`/dev/sda1`, `/dev/sda2`, etc.).

### Ejemplo de salida con `fdisk` en GPT:
```
Device      Start       End       Sectors    Size   Type
/dev/sda1   2048        1050623   1048576    512M   Linux filesystem
/dev/sda2   1050624     2097151   1046528    512M   Linux filesystem
/dev/sda3   2097152     31457279  29360128   14G    Linux filesystem
```

---

## Comparación de Errores al Crear Extendidas

| **Situación**                     | **MBR**                        | **GPT**                                    |
|-----------------------------------|---------------------------------|-------------------------------------------|
| Intentar crear extendida          | Permitido y funcional.          | Muestra error (`Partition type 'e' not supported`). |
| Crear partición lógica fuera de extendida | No posible, requiere una extendida. | No aplicable, no hay particiones lógicas. |

---

## Resumen Conceptual
- **MBR**: Necesita particiones extendidas y lógicas si se requieren más de 4 particiones. Son compatibles y se gestionan fácilmente.
- **GPT**: No requiere ni soporta particiones extendidas o lógicas. Gestiona todas las particiones como primarias, eliminando esta complicación.


