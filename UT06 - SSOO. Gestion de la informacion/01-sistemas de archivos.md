
# Sistemas de Archivos: Conceptos Básicos

## ¿Qué es un sistema de archivos?

Un sistema de archivos es una forma de organizar, gestionar y almacenar información en dispositivos de almacenamiento como discos duros, memorias USB o tarjetas SD. 

Es un software que actúa como un intermediario entre el hardware (donde físicamente están los datos) y el usuario o los programas que necesitan acceder a ellos.

---

## ¿Para qué utilizamos los sistemas de archivos?

1. **Almacenamiento:** Nos permite guardar información (documentos, fotos, vídeos, etc.) de manera estructurada.
2. **Organización:** Proporciona una forma lógica de dividir los datos en archivos y carpetas para encontrarlos fácilmente.
3. **Acceso:** Nos permite leer y escribir datos en el almacenamiento de manera sencilla.
4. **Gestión del espacio:** Decide cómo usar eficientemente el espacio de almacenamiento del dispositivo.
5. **Protección:** Ayuda a proteger los datos mediante permisos de acceso, restricciones y seguridad.

Sin un sistema de archivos, los datos en el almacenamiento serían una gran masa de ceros y unos, y no habría forma de diferenciarlos ni organizarlos.

---

## ¿Cómo funciona un sistema de archivos?

El sistema de archivos utiliza una combinación de estructuras y procesos para gestionar los datos:

1. **División del almacenamiento:**
   - El almacenamiento físico (como un disco duro) se divide en partes más pequeñas llamadas bloques.
   - Cada bloque puede guardar una cantidad fija de datos.

2. **Índice de archivos:**
   - El sistema mantiene un "registro" que dice qué bloques están ocupados, qué archivos están en ellos y cómo están relacionados.
   - Este registro incluye el nombre del archivo, su tamaño, tipo, ubicación, fecha de creación y permisos de acceso.

3. **Organización jerárquica:**
   - Los datos se organizan en **directorios** (también llamados carpetas) y **archivos**. Los directorios pueden contener otros directorios (subdirectorios), formando una estructura en forma de árbol.

4. **Traducción de rutas:**
   - Cuando un usuario busca un archivo (por ejemplo, un documento llamado "Trabajo.docx"), el sistema traduce esa solicitud en una ubicación específica dentro del almacenamiento físico.

---

## Archivos, directorios y rutas

### 1. Archivos

- **Definición:** Un archivo es una unidad de información guardada en el sistema de archivos. Puede contener texto, imágenes, música, programas, etc.
- **Propiedades:** Cada archivo tiene un nombre y una extensión que indica su tipo (`documento.txt`, `imagen.jpg`).
- **Ubicación:** Los archivos se guardan dentro de directorios.

---

### 2. Directorios

- **Definición:** Un directorio, o carpeta, es un contenedor que organiza archivos y otros directorios en una estructura jerárquica.
- **Jerarquía:** La estructura jerárquica permite clasificar archivos según su tipo o uso.
  - **Directorio raíz (root):** Es el punto de partida de todo el sistema de archivos.
  - **Subdirectorios:** Son carpetas dentro de otras carpetas.

Ejemplo:
```
/
├── Documentos
│   ├── Trabajo.docx
│   ├── Notas.txt
├── Imágenes
│   ├── Foto1.jpg
│   ├── Foto2.png
└── Música
    ├── Canción.mp3
```

En este ejemplo:
- `/` es el directorio raíz.
- `Documentos`, `Imágenes` y `Música` son directorios.
- `Trabajo.docx` es un archivo dentro del directorio `Documentos`.

---

### 3. Rutas

Una ruta es la dirección que indica dónde se encuentra un archivo o directorio en el sistema de archivos.

#### Tipos de rutas:

1. **Ruta absoluta:**
   - Define la ubicación completa de un archivo o directorio desde el directorio raíz.
   - Siempre comienza con el símbolo `/` (en sistemas Linux/macOS) o con una unidad como `C:\` (en Windows).
   - Ejemplo en Linux/macOS: `/Documentos/Trabajo.docx`
   - Ejemplo en Windows: `C:\Documentos\Trabajo.docx`

2. **Ruta relativa:**
   - Define la ubicación de un archivo o directorio desde la posición actual del usuario en el sistema de archivos.
   - No comienza desde el directorio raíz, sino desde el directorio donde el usuario está trabajando.
   - Ejemplo:
     - Si estás en `/Documentos` y quieres acceder a `Trabajo.docx`, la ruta relativa sería `Trabajo.docx`.
     - Si estás en `/Imágenes` y quieres ir a `Foto1.jpg`, la ruta relativa sería `../Documentos/Trabajo.docx` (donde `..` significa "subir un nivel").

---

### Diferencias clave entre rutas absolutas y relativas:

| Característica        | Ruta Absoluta                     | Ruta Relativa          |
|-----------------------|-----------------------------------|------------------------|
| **Punto de inicio**   | Comienza desde el directorio raíz | Comienza desde el directorio actual |
| **Simplicidad**       | Más clara, pero más larga         | Más corta, pero depende de la ubicación actual |
| **Ejemplo** (Linux)   | `/home/usuario/Documentos`        | `Documentos`           |

---

