# Herramienta a Explorar: FTK Imager Lite

**Objetivo:** Aprender a utilizar `FTK Imager Lite` para crear una imagen forense de una unidad USB, un paso fundamental para preservar la evidencia digital y mantener la Cadena de Custodia.

---

### ¿Qué es FTK Imager?

FTK Imager es una herramienta de adquisición de evidencia digital (imaging) que crea copias bit a bit de un dispositivo de almacenamiento. Una imagen forense es una copia exacta, sector por sector, que no altera la evidencia original.

**Características Clave:**
*   **No intrusivo:** Puede ejecutarse desde una unidad externa sin instalarse en la máquina del sujeto, evitando así la alteración de datos.
*   **Verificación de integridad:** Genera valores hash (MD5, SHA1) del dispositivo original y de la imagen creada. Si los hashes coinciden, se prueba que la copia es idéntica al original. Esto es crucial para la validez de la evidencia.
*   **Soporte para múltiples formatos:** Puede crear imágenes en formatos estándar de la industria forense como RAW (dd), E01 (EnCase) y AFF.

### Preparación en Kali Linux

Aunque FTK Imager es una herramienta para Windows, es fundamental saber cómo usarla, ya que a menudo se encontrará en entornos de respuesta a incidentes. Puedes ejecutarla en una máquina virtual de Windows o a través de Wine en Linux, aunque se recomienda usarla en un entorno nativo de Windows para garantizar su correcto funcionamiento.

**Descarga:**
1.  Busca `FTK Imager Lite` en la web de su desarrollador (Exterro).
2.  Descarga la versión "Lite", que no requiere instalación.
3.  Guarda los archivos en una unidad USB dedicada para tus herramientas forenses.

### Actividad Práctica: Crear una Imagen Forense de un Pendrive (USB)

**Materiales:**
*   Una computadora (preferiblemente con Windows o una VM de Windows).
*   La unidad USB con `FTK Imager Lite`.
*   Un pendrive (USB) que servirá como "evidencia".
*   Un disco duro externo o una ubicación con suficiente espacio para guardar la imagen.

**Pasos:**

1.  **Conectar Dispositivos:** Conecta el pendrive "evidencia" y el disco de destino a la computadora.

2.  **Ejecutar FTK Imager:** Abre la carpeta de `FTK Imager Lite` y ejecuta el programa.

3.  **Crear Imagen de Disco:**
    *   En el menú, ve a **File -> Create Disk Image...**.

4.  **Seleccionar Fuente:**
    *   Selecciona **Physical Drive** como tipo de fuente.
    *   En la siguiente ventana, elige de la lista el pendrive "evidencia" que quieres clonar. **¡Ten mucho cuidado de seleccionar la unidad correcta!**

5.  **Añadir Destino de Imagen:**
    *   Haz clic en el botón **Add...**.
    *   Selecciona el tipo de formato de imagen. **E01** es una excelente opción, ya que comprime la imagen y contiene metadatos para la cadena de custodia. **RAW (dd)** también es un formato común.
    *   Completa la información de la evidencia (número de caso, nombre del examinador, descripción, etc.). Esto es crucial para la documentación.
    *   Elige la carpeta de destino en tu disco duro externo donde se guardará la imagen y asígnale un nombre.

6.  **Iniciar la Adquisición:**
    *   Haz clic en **Start**. FTK Imager comenzará el proceso de creación de la imagen.
    *   El programa te mostrará el progreso y la velocidad de lectura.

7.  **Verificación Final:**
    *   Una vez completado el proceso, FTK Imager mostrará una ventana de resumen.
    *   Lo más importante es la sección **"Hashes verification"**. Comprueba que los hashes **MD5/SHA1** "Computed" (calculados desde la imagen creada) coinciden con los "Reported" (calculados desde la unidad original).
    *   **¡Si los hashes coinciden, has creado una copia forense verificada!** Guarda el archivo de registro (`.txt`) que se crea junto a la imagen, ya que contiene esta información de verificación.

**Conclusión de la Actividad:**
Al completar estos pasos, has realizado una de las tareas más fundamentales en el análisis forense digital: la adquisición de evidencia de una manera que garantiza su integridad y es admisible en una investigación.