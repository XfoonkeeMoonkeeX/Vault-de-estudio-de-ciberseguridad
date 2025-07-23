# La Telemetría como Terreno de Caza

> [!QUOTE] "Los datos son el terreno. Sin una visión clara del terreno, el cazador está ciego."

La **telemetría** se refiere a la corriente continua de datos de eventos que se recopilan de los sistemas para su monitorización. Para un Threat Hunter, esta telemetría es el conjunto de pistas que le permite reconstruir las acciones de un adversario. Las tres categorías principales de fuentes de datos son el Endpoint, la Red y la Identidad.

---

### 1. Endpoint: La Escena del Crimen Principal

El endpoint (estaciones de trabajo, servidores) es donde ocurre la mayor parte de la acción. Es la fuente de datos más rica y de más alta fidelidad.

-   **Logs de Creación de Procesos (Event ID 4688 en Windows, Sysmon Event ID 1):**
    -   **¿Qué es?** Un registro de cada vez que un programa se ejecuta.
    -   **Valor para el Hunter:** Es la fuente más importante. Permite ver qué proceso inició a qué otro (relaciones padre-hijo). Un `winword.exe` (Word) que de repente inicia un `powershell.exe` es extremadamente sospechoso.
-   **Logs de PowerShell (Módulos de Script Block Logging y Transcripción):**
    -   **¿Qué es?** PowerShell puede registrar cada bloque de código que se ejecuta, incluso si está ofuscado o se ejecuta en memoria.
    -   **Valor para el Hunter:** Proporciona una visibilidad completa de los ataques "sin fichero" (fileless) y del abuso de herramientas legítimas, una táctica favorita de los atacantes modernos.
-   **Registros del Sistema (Registry) en Windows:**
    -   **¿Qué es?** Una base de datos jerárquica que almacena la configuración del sistema operativo y de las aplicaciones.
    -   **Valor para el Hunter:** Es el lugar predilecto de los atacantes para lograr **persistencia**. El Hunter buscará la creación o modificación de claves de registro conocidas por ser abusadas (ej. `Run`, `RunOnce`).
-   **Logs de Sysmon:** (Ver nota [[Herramienta a Dominar - Sysmon]]). Es la fuente de datos de endpoint por excelencia.

---

### 2. Red: Las Rutas de Escape y Comunicación

Los datos de red proporcionan el contexto de cómo se comunican los endpoints entre sí y con el mundo exterior.

-   **Logs de Firewall y Proxy:**
    -   **¿Qué es?** Registros de todas las conexiones permitidas y bloqueadas que entran y salen de la red. Los logs de proxy registran específicamente las visitas a sitios web.
    -   **Valor para el Hunter:** Permite detectar comunicaciones con servidores de Comando y Control (C2) conocidos, intentos de escaneo desde IPs externas, o conexiones salientes a países o puertos inusuales.
-   **Logs de DNS:**
    -   **¿Qué es?** Un registro de cada vez que un equipo interno pide "traducir" un nombre de dominio (ej. `www.google.com`) a una dirección IP.
    -   **Valor para el Hunter:** Es una mina de oro. Los atacantes a menudo usan dominios generados algorítmicamente (DGA) para sus C2. Buscar peticiones DNS a dominios extraños, largos o con patrones aleatorios es una técnica de caza muy efectiva.
-   **Netflow:**
    -   **¿Qué es?** Es un resumen estadístico del tráfico de red. No contiene el contenido de los paquetes (no es PCAP), pero sí los metadatos: quién habló con quién, en qué puerto, cuántos datos se transfirieron y durante cuánto tiempo.
    -   **Valor para el Hunter:** Excelente para obtener una visión general y detectar anomalías, como una estación de trabajo que de repente empieza a enviar gigabytes de datos a un destino externo (posible exfiltración).
-   **PCAP (Captura Completa de Paquetes):**
    -   **¿Qué es?** Grabar cada bit y byte que pasa por la red.
    -   **Valor para el Hunter:** Es la fuente más detallada, pero también la más costosa de almacenar y analizar. Se suele usar de forma dirigida durante una investigación activa, no para un monitoreo continuo de toda la red.

---

### 3. Identidad: Las Llaves del Reino

Los sistemas de identidad controlan quién es quién y a qué tiene acceso. Comprometerlos es a menudo el objetivo principal de un atacante.

-   **Logs de Autenticación (Active Directory, VPN, SSO):**
    -   **¿Qué es?** Registros de cada intento de inicio de sesión, tanto exitoso como fallido.
    -   **Valor para el Hunter:** Permite cazar ataques de fuerza bruta (múltiples fallos), movimiento lateral (un administrador que inicia sesión en una estación de trabajo normal, lo cual es inusual), o uso de cuentas comprometidas desde ubicaciones geográficas extrañas.