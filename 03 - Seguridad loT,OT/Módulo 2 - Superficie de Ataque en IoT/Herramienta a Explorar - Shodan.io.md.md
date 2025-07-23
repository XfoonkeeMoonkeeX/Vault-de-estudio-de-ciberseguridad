# 🛠️ Herramienta a Explorar: Shodan.io

> [!tool] ¿Qué es?
> Shodan no es un motor de búsqueda como Google que indexa contenido web. Shodan es un **motor de búsqueda de dispositivos**. Recorre internet constantemente y escanea direcciones IP en busca de puertos abiertos. Cuando encuentra un puerto abierto, "conversa" con el servicio que está escuchando en ese puerto y captura el **banner**, que es la información de bienvenida que el servicio ofrece. Es el "Google de los hackers".

### ¿Cómo Usar Shodan? (Búsquedas Básicas)

Necesitarás crear una cuenta gratuita en [https://www.shodan.io/](https://www.shodan.io/) para poder usar los filtros, que es donde reside su verdadero poder.

**Filtros Clave:**
-   `product:"nginx"`: Busca todos los dispositivos que ejecutan el servidor web Nginx.
-   `port:22`: Busca todos los dispositivos con el puerto 22 (SSH) abierto.
-   `country:"CL"`: Busca dispositivos ubicados en un país específico (ej. Chile).
-   `city:"Santiago"`: Filtra por ciudad.
-   `org:"Google LLC"`: Filtra por organización o proveedor de servicios de internet.
-   `vuln:CVE-2021-44228`: Busca dispositivos que Shodan ha identificado como potencialmente vulnerables a un CVE específico (esta es una función muy potente).

Puedes combinar filtros para refinar tu búsqueda. Por ejemplo, `product:"Apache httpd" country:"ES"` buscará servidores Apache en España.

### La Caza de Dispositivos IoT

Shodan es increíblemente útil para encontrar dispositivos IoT inseguros expuestos al mundo.

**Búsquedas de Ejemplo:**
-   **Cámaras Web Inseguras:**
    -   Muchas cámaras web tienen títulos de página o respuestas de servidor predecibles.
    -   Prueba a buscar: `webcamxp` o `server: "webcam"` o `http.title:"Webcam"`.
-   **Routers con Contraseñas por Defecto:**
    -   Busca el banner de autenticación HTTP por defecto de un modelo de router específico.
    -   Prueba a buscar: `http.title:"router configuration"`
-   **Sistemas de Control Industrial (SCADA):**
    -   **¡PRECAUCIÓN!** Interactuar con estos sistemas es ilegal y peligroso. Estas búsquedas son solo para fines educativos de concienciación.
    -   Busca por protocolos de OT: `port:502` (Modbus).
    -   Busca por productos de HMI: `product:"Pro-face HMI"`

### ¿Por qué es tan valioso para un analista?

-   **Reconocimiento:** Antes de un pentest, puedes usar Shodan para ver qué servicios expone un cliente.
-   **Inteligencia de Amenazas:** Puedes monitorear la propagación de una vulnerabilidad viendo cuántos dispositivos vulnerables hay expuestos.
-   **Concienciación:** Demuestra de forma gráfica y aterradora cuántos dispositivos inseguros están conectados directamente a internet, accesibles para cualquiera.