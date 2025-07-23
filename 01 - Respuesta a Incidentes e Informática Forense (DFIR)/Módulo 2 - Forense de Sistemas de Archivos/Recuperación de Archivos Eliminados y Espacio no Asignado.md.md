# Recuperación de Archivos Eliminados y Espacio no Asignado

> [!QUOTE] "Borrar no es destruir. Es simplemente olvidar dónde pusiste algo."

Cuando un usuario "elimina" un archivo (ej. vaciando la papelera de reciclaje), el sistema operativo no borra los datos físicamente del disco. Simplemente marca el espacio que ocupaban como "disponible" para ser sobrescrito en el futuro.

### ¿Cómo funciona la eliminación?

-   **En NTFS:** La entrada del archivo en la **MFT** se marca como "no en uso". Los punteros a los clústeres de datos se eliminan, pero los datos en sí permanecen intactos en el disco.
-   **En ext4:** El **inodo** del archivo se marca como "libre". Los punteros a los bloques de datos se borran.

En ambos casos, los datos reales persisten hasta que el sistema operativo necesita ese espacio para escribir un nuevo archivo.

### Espacio no Asignado (Unallocated Space)

-   **Definición:** Es la porción del disco que el sistema de archivos considera vacía y disponible, pero que puede contener (y a menudo contiene) datos completos o fragmentos de archivos eliminados.
-   **Valor Forense:** El espacio no asignado es un tesoro para un investigador. Aquí podemos encontrar documentos borrados, correos electrónicos, imágenes, historial de internet, etc.

### File Carving (Tallado de Archivos)

-   **¿Qué es?** Es la técnica que utilizan las herramientas forenses para recuperar archivos del espacio no asignado.
-   **¿Cómo funciona?** El software (como Autopsy) escanea el espacio no asignado byte por byte buscando **encabezados (headers)** y **pies de página (footers)** de archivos conocidos. Por ejemplo, todos los archivos JPEG comienzan con los bytes `FF D8` y terminan con `FF D9`. Cuando Autopsy encuentra un encabezado, "talla" los datos que le siguen hasta encontrar el pie de página (o hasta un tamaño máximo definido), recuperando así el archivo eliminado.