
# Gestión de Discos y Particiones en Ubuntu

### **Directorio de trabajo: `/dev`**
En Ubuntu, los discos, particiones y otros dispositivos de almacenamiento se representan como archivos especiales en el directorio **`/dev`**. Cada disco y partición tiene un nombre asignado:

- **Discos**:
  - `/dev/sda`: Representa el primer disco físico detectado.
  - `/dev/sdb`: Representa el segundo disco físico, y así sucesivamente.

- **Particiones**:
  - `/dev/sda1`: La primera partición del disco `/dev/sda`.
  - `/dev/sda2`: La segunda partición del disco `/dev/sda`, y así sucesivamente.

El directorio `/dev` es clave porque todas las operaciones relacionadas con discos y particiones apuntan a estos nombres de dispositivo.

---

### **Montar y Desmontar un Disco**
#### **¿Qué significa montar un disco?**
Montar un disco significa **hacer accesible un sistema de archivos** al sistema operativo, asignándolo a un directorio específico. Por ejemplo, al montar `/dev/sda1` en `/mnt`, los archivos en esa partición serán accesibles a través del directorio `/mnt`.

#### **¿Qué significa desmontar un disco?**
Desmontar un disco significa **desasociarlo de su punto de montaje**. Esto libera el dispositivo y asegura que no haya procesos en uso, evitando corrupción de datos.

---

### **Directorio `/mnt`**
El directorio **`/mnt`** es un punto de montaje estándar utilizado en Ubuntu. Su propósito principal es proporcionar un lugar temporal para montar sistemas de archivos manualmente.

- **Usos típicos**:
  - Montar discos adicionales, como particiones o unidades USB, para realizar tareas específicas.
  - Realizar pruebas con discos o particiones antes de configurarlas permanentemente.
  - Acceder a particiones dañadas o discos externos.

Ejemplo:
```bash
sudo mount /dev/sda1 /mnt
```
Este comando monta la partición `/dev/sda1` en `/mnt`, permitiendo acceder a sus datos en esa ubicación.

---

### **Listado detallado de comandos**

#### **1. Listar discos y particiones**
- **Comando**: `fdisk`
- **Descripción**: Muestra los discos y particiones conectados al sistema, junto con detalles como tamaño, tipo y esquema de partición.
- **Sintaxis**:
  ```bash
  sudo fdisk -l
  ```
- **Uso típico**:
  - Ver todos los discos y particiones disponibles en el sistema.
  - Identificar el disco que deseas manipular, verificando el tamaño, particiones y nombres de dispositivos.

**Ejemplo de salida de `sudo fdisk -l`:**
```
Disk /dev/sda: 500 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

Device      Boot   Start       End       Blocks    Id  System
/dev/sda1   *      2048       1050623   524288    83  Ubuntu
/dev/sda2          1050624    2097151   524288    83  Ubuntu
/dev/sda3          2097152    976773167 487837008 5   Extended
/dev/sda5          2101248    31457279  14656016  83  Ubuntu
```
- En este ejemplo:
  - `/dev/sda`: Disco de 500 GB.
  - `/dev/sda1`, `/dev/sda2`: Particiones principales.
  - `/dev/sda3`: Partición extendida que contiene particiones lógicas `/dev/sda5`.

---

#### **2. Montar un disco o partición**
- **Comando**: `mount`
- **Descripción**: Monta un sistema de archivos en un directorio del sistema operativo.
- **Sintaxis**:
  ```bash
  sudo mount [opciones] dispositivo directorio
  ```
- **Uso típico**:
  - Montar una partición para acceder a sus archivos:
    ```bash
    sudo mount /dev/sda1 /mnt
    ```
    Esto monta la partición `/dev/sda1` en el directorio `/mnt`.
  - Montar un disco USB automáticamente:
    ```bash
    sudo mount /dev/sdb1 /media/usb
    ```

---

#### **3. Desmontar un disco o partición**
- **Comando**: `umount`
- **Descripción**: Desmonta un sistema de archivos, liberando el dispositivo para otras operaciones.
- **Sintaxis**:
  ```bash
  sudo umount dispositivo_o_directorio
  ```
- **Uso típico**:
  - Desmontar una partición montada en `/mnt`:
    ```bash
    sudo umount /mnt
    ```
  - Desmontar una partición por su nombre de dispositivo:
    ```bash
    sudo umount /dev/sda1
    ```

---

#### **4. Crear una nueva partición**
- **Comando**: `fdisk`
- **Descripción**: Permite gestionar particiones en discos (crear, eliminar, redimensionar).
- **Sintaxis**:
  ```bash
  sudo fdisk dispositivo
  ```
- **Uso típico**:
  1. Iniciar la herramienta para un disco:
     ```bash
     sudo fdisk /dev/sda
     ```
  2. Crear una nueva partición interactiva:
     - Pulsa `n` para nueva partición.
     - Selecciona tipo (`p` para primaria, `e` para extendida).
     - Define el tamaño.

---

#### **5. Formatear una partición**
- **Comando**: `mkfs`
- **Descripción**: Crea un sistema de archivos en una partición.
- **Sintaxis**:
  ```bash
  sudo mkfs.tipo /dev/dispositivo
  ```
- **Tipos de sistemas de archivos compatibles (ejemplo):**
  - **ext4**: Sistema de archivos moderno y robusto para Ubuntu.
  - **ntfs**: Sistema usado en Windows.
  - **vfat (FAT32)**: Sistema compatible con Windows, Ubuntu y dispositivos como USB.

**Uso típico**:
1. Formatear una partición en ext4:
   ```bash
   sudo mkfs.ext4 /dev/sda1
   ```
2. Formatear una partición en NTFS:
   ```bash
   sudo mkfs.ntfs /dev/sda1
   ```
3. Formatear una partición en FAT32:
   ```bash
   sudo mkfs.vfat /dev/sda1
   ```

---

#### **6. Redimensionar una partición**
- **Comando**: `resize2fs`
- **Descripción**: Ajusta el tamaño del sistema de archivos ext2, ext3 o ext4.
- **Sintaxis**:
  ```bash
  sudo resize2fs dispositivo tamaño
  ```
- **Uso típico**:
  1. Reducir el tamaño de una partición a 20 GB:
     ```bash
     sudo resize2fs /dev/sda1 20G
     ```
  2. Ampliar una partición al máximo espacio disponible:
     ```bash
     sudo resize2fs /dev/sda1
     ```

---

#### **7. Verificar y reparar un sistema de archivos**
- **Comando**: `e2fsck`
- **Descripción**: Verifica y repara sistemas de archivos ext2, ext3 o ext4.
- **Sintaxis**:
  ```bash
  sudo e2fsck -f dispositivo
  ```
- **Uso típico**:
  - Verificar un sistema de archivos y reparar errores automáticamente:
    ```bash
    sudo e2fsck -f /dev/sda1
    ```
  - Uso común antes de redimensionar particiones.

---