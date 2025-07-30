# Adquisición de Memoria (Windows y Linux)

> [!WARNING] ¡Proceso Crítico!
> La adquisición de memoria (o "memory dump") es un proceso delicado. La propia herramienta que usamos para hacer el volcado alterará mínimamente la memoria que estamos tratando de preservar. El objetivo es minimizar esta alteración y realizar la captura de la forma más limpia posible.

El proceso implica ejecutar una herramienta de confianza en la máquina "viva" (live system) para copiar el contenido completo de la RAM a un archivo en un dispositivo de almacenamiento externo.

### Adquisición en un Sistema Windows

Las herramientas para Windows suelen ser ejecutables portátiles que se pueden correr desde una unidad USB para no instalar nada en el sistema sospechoso.

**Herramientas Populares:**
-   **FTK Imager Lite:** Una de las herramientas más conocidas de la empresa AccessData. Es gratuita y muy fiable. Permite capturar la memoria y guardarla en un archivo con formato `.mem`.
-   **Belkasoft RAM Capturer:** Otra herramienta gratuita y fácil de usar, diseñada específicamente para la captura de memoria de 32 y 64 bits.
-   **WinPmem:** Parte del conjunto de herramientas de `pmem`. Es de código abierto y muy utilizado en el ámbito forense.

**Proceso General:**
1.  Colocar la herramienta en una unidad USB externa.
2.  Conectar la unidad USB al sistema Windows encendido.
3.  Ejecutar la herramienta de captura con privilegios de administrador.
4.  Especificar la unidad USB externa como destino para el archivo de volcado de memoria.
5.  Esperar a que el proceso se complete. El archivo resultante será del mismo tamaño que la RAM instalada (ej. 8 GB de RAM = archivo de 8 GB).

---

### Adquisición en un Sistema Linux

En Linux, el proceso a menudo implica cargar un módulo del kernel.

**Herramientas Populares:**
-   **LiME (Linux Memory Extractor):** Es el estándar de facto para la adquisición de memoria en Linux. Es un Módulo del Kernel Cargable (LKM) que, una vez compilado para la versión específica del kernel de la máquina objetivo, se inserta para crear el volcado.
-   **AVML (Acquire Volatile Memory for Linux):** Una herramienta más nueva escrita en Rust, diseñada para ser más fácil de usar que LiME, ya que a menudo no requiere compilar un módulo para cada kernel.

**Proceso General (con LiME):**
1.  Compilar el módulo de LiME para la arquitectura y versión del kernel del sistema objetivo.
2.  Copiar el módulo compilado (`.ko`) a la máquina objetivo.
3.  Insertar el módulo en el kernel, especificando la ruta de destino y el formato.
    ```bash
    # Ejemplo de comando para insertar el módulo
    sudo insmod lime.ko "path=/mnt/usb_externa/memdump.lime format=lime"
    ```
4.  Una vez completado el volcado, retirar el módulo del kernel.
    ```bash
    sudo rmmod lime
    ```
