# Análisis de Sistemas de Archivos (NTFS y ext4)

> [!QUOTE] "Un sistema de archivos es el mapa de una ciudad digital. Como forenses, nuestro trabajo es leer ese mapa para encontrar dónde se esconde la evidencia."

Un sistema de archivos organiza cómo se almacenan y recuperan los datos en un dispositivo. Cada uno tiene estructuras únicas que, desde un punto de vista forense, son una mina de oro de artefactos y metadatos.

---

### Windows: NTFS (New Technology File System)

Es el sistema de archivos estándar en los sistemas operativos Windows modernos. Todo en NTFS se considera un "archivo", incluso los propios metadatos del sistema.

**Artefactos Forenses Clave:**
-   **Master File Table (MFT):** Es el corazón de NTFS. La MFT es una tabla que contiene al menos una entrada por cada archivo en el volumen. Cada entrada registra los atributos del archivo: nombre, tamaño, timestamps (tiempos MAC) y, lo más importante, punteros a la ubicación física de los datos del archivo en el disco. El análisis de la MFT es fundamental para encontrar archivos, incluidos los eliminados.
-   **Timestamps:** NTFS almacena timestamps muy detallados (ver nota [[Timestamps MAC (Modified, Accessed, Created)]]).
-   **Alternate Data Streams (ADS):** Una característica de NTFS que permite almacenar datos "detrás" de un archivo normal. Los atacantes a menudo usan ADS para ocultar malware o herramientas, ya que no son visibles en el explorador de archivos estándar.
-   **Volume Shadow Copies:** Son instantáneas de un volumen que Windows crea para restauración. A menudo contienen versiones antiguas de archivos que un usuario pudo haber modificado o eliminado, permitiéndonos recuperar evidencia pasada.

---

### Linux: ext4 (Fourth Extended Filesystem)

Es el sistema de archivos por defecto en la mayoría de las distribuciones de Linux, incluida Kali. Su estructura es diferente a la de NTFS.

**Artefactos Forenses Clave:**
-   **Inodos (Inodes):** Similar a una entrada MFT, un inodo es una estructura de datos que almacena toda la información sobre un archivo (metadatos como permisos, propietario, timestamps), excepto su nombre y sus datos. Cada archivo tiene un número de inodo único.
-   **Bloques de datos (Data Blocks):** Son las unidades donde se almacena el contenido real del archivo. El inodo contiene punteros que indican qué bloques de datos pertenecen al archivo.
-   **Superbloque (Superblock):** Contiene información crítica sobre todo el sistema de archivos, como el número total de inodos y bloques, y el tamaño del bloque. Si el superbloque se corrompe, el sistema de archivos puede volverse ilegible.
-   **Journal:** Es un registro de los cambios que están a punto de realizarse en el sistema de archivos. En una investigación, el journal puede contener fragmentos de datos o metadatos de archivos que existieron por un corto período.
