
# Práctica 04. Creación y gestión de particiones

**Objetivo del taller**  
El objetivo de esta práctica es aplicar conocimientos de gestión de discos y particiones utilizando herramientas en Ubuntu. 

Además, se utilizarán ciertos directorios para realizar esta práctica que se han visto en clase, por lo que es interesante ser capaz de relacionarlos.

Las tareas que se realizarán estarán guiadas con este enunciado y se dispone de ficheros de documentación que puedan ayudar a identificar los comandos y argumentos a utilizar.

El entorno utilizado es la máquina virtual con el programa Virtual Box con la ISO de Ubuntu y con GParted como herramienta externa donde se realizarán operaciones como redimensionar particiones, crear sistemas de archivos y comprobar configuraciones.

---

## **Desarrollo de la práctica**

### **Fase 1: Comprobación del entorno**
1. **Verificación inicial:**
   - Asegúrate de que tienes una **máquina virtual con Ubuntu previamente instalada** con las condiciones necesarias para la realización de la práctica.
   - Si no está creada, configúrala siguiendo estos parámetros:
     - Disco virtual de al menos **10 GB**.
     - **Una única partición** primaria que ocupe todo el espacio del disco.

2. **Comprobación de configuración:**
   - Inicia sesión en la máquina virtual y verifica la configuración del disco.
   - Usa una herramienta de gestión de particiones en Ubuntu para comprobar la existencia de una única partición que ocupe todo el disco.  
     - **Pista:** Puedes usar `fdisk` para realizar esta comprobación.  
   - Documenta esta comprobación con capturas de pantalla donde se muestren:
     - El tamaño del disco.
     - La partición principal.

---

### **Fase 2: Intento de redimensionar la partición principal**
1. **Redimensionar partición en Ubuntu:**
   - Intenta reducir la partición primaria utilizando un comando que permita redimensionar sistemas de archivos en Ubuntu.  
     - **Pista:** El comando que necesitas usar es `resize2fs`.  
   - Comprueba si la partición se redimensiona correctamente o si ocurre algún error.
   - Si no es posible redimensionar, **explica detalladamente** los motivos del error y documenta esta parte con capturas de pantalla.

2. **Configuración de entorno externo:**
   - Prepara un **USB booteable** con una herramienta externa como **GParted**. Puedes usar herramientas como **Ventoy**, **Rufus** u otra herramienta similar para configurar el USB.
   - Descarga la ISO de **GParted Live** de la web oficial. 
   - Monta la ISO de **GParted Live** en la máquina virtual y reinicia para arrancar desde el dispositivo USB.

---

### **Fase 3: Redimensionar la partición principal con GParted**
1. **Acceso a GParted:**
   - Una vez iniciada la máquina virtual desde el entorno GParted:
     - Localiza la partición principal que ocupa todo el espacio del disco.
     - Reduce su tamaño y libera **2 GB**.
     - Aplica los cambios y confirma que se realiza correctamente.

2. **Verificación de particiones:**
   - Reinicia la máquina virtual y verifica nuevamente las particiones utilizando herramientas disponibles en Ubuntu.
     - **Pista:** Usa `fdisk` para listar las particiones y comprobar el espacio disponible.  
   - Si el resultado no es **concluyente** (se visualiza claramente ambas particiones y espacio), complementa la verificación usando la **herramienta gráfica de discos** de Ubuntu. Documenta los resultados.

---

### **Fase 4: Crear una partición principal y comprobar funcionalidad**
1. **Crear una partición principal:**
   - Usa el espacio de **2 GB libres** para crear una nueva partición primaria.
   - Usa los comandos necesarios para formatear la partición con un sistema de archivos adecuado para Ubuntu.
     - **Pista:** El comando que necesitas usar es `mkfs`.  
   - Monta la partición en un directorio como `/mnt`.
   - Verifica que la partición es funcional creando un archivo de prueba. Dos formas:
      - Realizarlo con comandos (suma mas)
      - Realizarlo gráficamente (suma menos)
   - Comprueba que el archivo existe. Dos formas:
      - Realizarlo con comandos (suma mas)
      - Realizarlo gráficamente (suma menos) 

2. **Documentación:**
   - Anota todos los pasos y comandos usados, y realiza capturas de pantalla del proceso.

---

### **Fase 5: Redimensionar la partición principal y crear una extendida**
1. **Redimensionar la partición de 2 GB a 1 GB:**
   - Dado que esta nueva partición ya no es la partición del sistema operativo, intenta redimensionar la partición de **2 GB** a **1 GB** utilizando los comandos adecuados.
     - **Pista:** Usa los comandos `resize2fs` y `fdisk` para completar esta tarea.

2. **Crear una partición extendida:**
   - Usa el espacio libre restante (**1 GB**) para crear una partición extendida.
   - Verifica si la particion se crea correctamente.

3. **Documentación:**
   - Anota los pasos realizados y adjunta capturas de pantalla mostrando las particiones finales.

---

## **Criterios de evaluación**
1. **Comprobación inicial (10%)**:
   - Configuración correcta del entorno y verificación del disco inicial.
   - Documentación completa con capturas de pantalla.

2. **Redimensionamiento inicial (20%)**:
   - Análisis del intento de redimensionar desde Ubuntu, con una explicación detallada de los resultados.
   - Configuración adecuada de GParted y USB booteable.

3. **Creación de partición funcional (25%)**:
   - Correcta configuración del sistema de archivos y pruebas funcionales.

4. **Redimensionamiento y creación de partición extendida (25%)**:
   - Ejecución correcta del proceso y configuración final de particiones.

5. **Documentación final (20%)**:
   - Informe con capturas claras, comandos usados y análisis de resultados.

---

### **Normas sobre las calificaciones máximas de la entrega**

La calificación máxima a la que se podrá optar  dependerá de la fecha y hora de entrega de la práctica. El criterio es el siguiente:

1. **Entrega en horario de clase (hasta hoy a las 18:15)**:
   - **Calificación máxima**: 10 puntos.

2. **Entrega el mismo día (hasta las 23:59 de hoy)**:
   - **Calificación máxima**: 9,5 puntos.

3. **Entrega en los días posteriores**:
   - Cada **2 días** la calificación máxima baja en **1 punto** hasta llegar al mínimo de **4 puntos**, que no se reducirá más.

   - **Calificaciones máximas según la fecha**:
- **17/12/2024** (hasta las 23:59): **8.5 puntos**
- **19/12/2024** (hasta las 23:59): **7.5 puntos**
- **21/12/2024** (hasta las 23:59): **6.5 puntos**
- **23/12/2024** (hasta las 23:59): **5.5 puntos**
- **25/12/2024** (hasta las 23:59): **4.0 puntos**

4. **Entrega fuera de plazo mínimo**:
   - Las entregas realizadas después de la fecha de evaluación final solo recibirán el puntaje mínimo, siempre y cuando cumplan con los requisitos básicos de la práctica.

Este sistema busca motivar la finalización de la práctica en tiempo y forma, valorando especialmente la habilidad con el entorno y el esfuerzo de quienes completan el ejercicio durante el horario de clase.
