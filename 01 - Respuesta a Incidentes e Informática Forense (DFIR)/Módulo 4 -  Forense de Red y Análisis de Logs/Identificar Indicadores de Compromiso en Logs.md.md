# Identificar Indicadores de Compromiso en Logs

> [!QUOTE] "Los logs son las huellas dactilares que los atacantes dejan en la escena del crimen digital."

Un **Indicador de Compromiso (IoC)** es una pieza de evidencia forense que, con alta confianza, indica que ha ocurrido una intrusión en el sistema. Los logs son una de las fuentes más ricas de IoCs.

### Tipos de Logs y los IoCs que Revelan

-   **Logs del Sistema Operativo:**
    -   **Windows Event Logs:** Se encuentran en el "Visor de Eventos". Buscamos:
        -   `ID 4625`: Múltiples intentos de inicio de sesión fallidos (posible ataque de fuerza bruta).
        -   `ID 4624`: Un inicio de sesión exitoso desde una IP o cuenta inesperada.
        -   `ID 7045`: Un nuevo servicio ha sido instalado (táctica común de persistencia de malware).
    -   **Linux Logs (`/var/log/`)**:
        -   `/var/log/auth.log`: Muestra intentos de login (SSH, sudo). Múltiples fallos son una bandera roja.
        -   `/var/log/syslog` o `/var/log/messages`: Log general del sistema, donde se puede ver la creación de procesos o errores inusuales.

-   **Logs de Firewall:**
    -   Registran el tráfico que es permitido o bloqueado al entrar o salir de la red.
    -   **IoCs Comunes:**
        -   Grandes cantidades de conexiones bloqueadas desde una misma IP (indica que estamos siendo escaneados).
        -   Conexiones salientes a direcciones IP conocidas por ser maliciosas (un equipo interno podría estar infectado y comunicándose con un C2).
        -   Tráfico en puertos no estándar o inusuales.

-   **Logs de Servidores Web (Apache, Nginx, IIS):**
    -   Registran cada petición HTTP recibida por el servidor.
    -   **IoCs Comunes:**
        -   Peticiones a páginas que no existen (ej. `/admin.php`, `/wp-login.php`), lo que indica un escaneo de vulnerabilidades.
        -   Patrones de Inyección SQL o Cross-Site Scripting (XSS) en las URLs.
        -   Códigos de respuesta `404` (No Encontrado) en grandes cantidades, o `500` (Error del Servidor) que pueden indicar un ataque exitoso.
        -   Peticiones de un mismo IP a una velocidad sobrehumana (indica un bot o script).