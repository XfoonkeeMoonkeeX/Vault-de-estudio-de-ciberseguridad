# Vulnerabilidades Comunes en Dispositivos IoT

> [!QUOTE] "Muchos dispositivos IoT son diseñados con la funcionalidad como única prioridad, tratando la seguridad como un pensamiento posterior... o inexistente."

Los dispositivos IoT a menudo sufren de vulnerabilidades básicas que han sido resueltas hace años en el mundo del desarrollo web y de servidores. Estas son algunas de las más peligrosas y recurrentes.

-   **1. Credenciales Débiles o por Defecto:**
    -   **El Problema:** Es, quizás, la vulnerabilidad más común. Muchos dispositivos vienen de fábrica con un nombre de usuario y contraseña fijos (ej. `admin`/`admin`, `root`/`password`). Los usuarios a menudo no los cambian, y los atacantes tienen listas de estas credenciales por defecto que prueban automáticamente.
    -   **Ejemplo:** La botnet Mirai se propagó masivamente explotando credenciales por defecto en cámaras y routers.

-   **2. Interfaces Web Inseguras:**
    -   **El Problema:** Muchos dispositivos IoT se gestionan a través de una interfaz web. Estas interfaces a menudo sufren de las mismas vulnerabilidades que las páginas web tradicionales (OWASP Top 10), como **Inyección de Comandos**, **XSS** y **Broken Access Control**.
    -   **Ejemplo:** Una interfaz web que no valida correctamente la entrada del usuario podría permitir a un atacante inyectar comandos del sistema operativo y tomar control total del dispositivo.

-   **3. Falta de Cifrado en la Comunicación:**
    -   **El Problema:** Los datos se transmiten en texto plano entre el dispositivo, la aplicación móvil y la nube. Esto permite a un atacante en la misma red (ej. un Wi-Fi público) realizar un ataque de "Man-in-the-Middle" para leer y manipular el tráfico.
    -   **Ejemplo:** Robar la contraseña de un usuario o incluso el stream de video de una cámara de seguridad.

-   **4. Actualizaciones de Firmware Inexistentes o Inseguras:**
    -   **El Problema:** El **firmware** es el software que corre en el dispositivo. Cuando se descubre una vulnerabilidad, el fabricante debe lanzar una actualización. Muchos dispositivos IoT de bajo coste:
        -   Nunca reciben actualizaciones.
        -   No tienen un mecanismo para actualizarse automáticamente (requieren que el usuario descargue y aplique el parche manualmente, lo cual casi nadie hace).
        -   El proceso de actualización en sí mismo es inseguro (ej. descarga el nuevo firmware por HTTP, sin firmar), permitiendo a un atacante instalar un firmware malicioso.

-   **5. Puertos y Servicios de Red Innecesarios:**
    -   **El Problema:** Los dispositivos a menudo dejan puertos de red abiertos que solo se usaron para depuración durante el desarrollo (como Telnet o FTP). Estos servicios suelen ser inseguros y proporcionan una puerta de entrada fácil para los atacantes.

-   **6. Secretos "Hardcodeados":**
    -   **El Problema:** Claves de API, credenciales o claves de cifrado privadas están escritas directamente en el código del firmware. Cualquiera que extraiga el firmware puede encontrar estos secretos.
