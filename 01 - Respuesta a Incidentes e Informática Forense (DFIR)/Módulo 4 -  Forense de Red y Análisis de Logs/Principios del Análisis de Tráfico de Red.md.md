# Principios del Análisis de Tráfico de Red

> [!QUOTE] "Los paquetes no mienten. Son la transcripción literal de una conversación digital."

El análisis de tráfico de red consiste en examinar los datos capturados de una red para entender qué comunicación ocurrió. Estos datos se guardan comúnmente en archivos de captura de paquetes, siendo `.pcap` (Packet Capture) el formato más famoso.

### Reconstrucción de Sesiones

-   **¿Qué es?** Las herramientas como Wireshark pueden tomar miles de paquetes individuales que forman parte de una misma conversación (como la carga de una página web) y reensamblarlos en un formato legible.
-   **"Follow TCP/HTTP/UDP Stream":** Esta es la función mágica que lo hace posible. Te permite ver la conversación tal y como la vieron las aplicaciones. Por ejemplo, puedes ver el código HTML de una página web, el texto de un chat no cifrado o los comandos enviados por un atacante.

### Reconstrucción de Archivos

-   **¿Qué es?** Si un archivo fue transferido a través de un protocolo no cifrado (como HTTP, FTP, SMB), los datos de ese archivo están contenidos dentro de los paquetes de la red.
-   **Extracción:** Las herramientas forenses de red pueden "tallar" (carve) estos datos de los paquetes y reconstruir el archivo original. Esto es increíblemente útil para extraer malware, documentos robados o cualquier otro archivo transferido durante un incidente. Por ejemplo, Wireshark tiene una función para exportar objetos de HTTP (`File > Export Objects > HTTP`).

### El Foco del Análisis

-   **Metadatos:** ¿Quién habló con quién? (IPs de origen y destino). ¿Cuándo hablaron? (Timestamps). ¿Cuánto tiempo hablaron? (Duración de la sesión). ¿Cuántos datos se transfirieron? (Tamaño de los paquetes).
-   **Contenido:** ¿Qué se dijeron? (El contenido real o *payload* de los paquetes). Esto solo es posible si el tráfico no está cifrado. Para el tráfico cifrado (HTTPS, SSH), no podemos ver el contenido, pero los metadatos siguen siendo extremadamente valiosos.