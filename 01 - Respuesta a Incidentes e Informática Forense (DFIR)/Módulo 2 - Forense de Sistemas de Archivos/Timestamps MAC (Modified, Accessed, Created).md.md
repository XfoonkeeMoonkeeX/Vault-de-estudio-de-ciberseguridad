# Timestamps MAC (Modified, Accessed, Created)

> [!QUOTE] "Los archivos mienten, pero los timestamps susurran la verdad."

Los timestamps son metadatos que registran cuándo ocurrieron ciertos eventos en un archivo o directorio. Son absolutamente cruciales para construir una **cronología de la actividad** de un usuario o un atacante. Se conocen como tiempos MAC.

### El Desglose:

-   **M - Modified (Modificado):**
    -   **¿Qué es?** La última vez que el **contenido** de un archivo fue alterado.
    -   **Ejemplo:** Si abres un documento de texto, escribes una palabra y lo guardas, el tiempo de modificación se actualiza.

-   **A - Accessed (Accedido):**
    -   **¿Qué es?** La última vez que el archivo fue abierto, leído o ejecutado.
    -   **¡CUIDADO!** En muchos sistemas modernos (incluidos Windows 10/11 y algunas configuraciones de Linux), este timestamp se deshabilita por defecto por razones de rendimiento. Si está disponible, es muy valioso, pero no siempre se puede confiar en él.

-   **C - Created / Changed (Creado / Cambiado):**
    -   Aquí hay una diferencia crítica entre Windows y Linux:
    -   **En Windows (NTFS):** Se le llama **Birth Time** (Tiempo de Nacimiento). Es la fecha en que el archivo fue **creado** en ese volumen específico.
    -   **En Linux (ext4):** Se le llama **Changed Time** (Tiempo de Cambio). Registra la última vez que los **metadatos** del archivo (su inodo) cambiaron. Esto incluye cambios de nombre, de permisos, de propietario, etc. **No es el tiempo de creación**.

### Valor Forense:

-   **Establecer la primera aparición:** El tiempo de creación puede indicar cuándo se descargó un malware por primera vez.
-   **Detectar actividad reciente:** El tiempo de acceso puede mostrar qué archivos vio un intruso.
-   **Confirmar manipulación de datos:** El tiempo de modificación muestra cuándo se alteró un archivo de registro o un documento.

Herramientas como Autopsy pueden visualizar estos timestamps en una línea de tiempo gráfica, haciendo muy fácil ver la secuencia de eventos.