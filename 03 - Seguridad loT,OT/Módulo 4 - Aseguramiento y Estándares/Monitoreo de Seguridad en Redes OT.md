# Monitoreo de Seguridad en Redes OT

> [!QUOTE] "En IT, escaneas para ver qué hay. En OT, si escaneas, puede que ya no haya nada."

El monitoreo de seguridad en redes OT es fundamental, pero debe hacerse con un cuidado extremo debido a la fragilidad de los dispositivos y la prioridad absoluta de la disponibilidad.

### El Peligro del Escaneo Activo

-   **¿Qué es el Escaneo Activo?** Es la técnica usada en redes de IT donde una herramienta (como `Nmap`) envía paquetes a los dispositivos para "preguntarles" activamente qué puertos tienen abiertos, qué servicios ejecutan, etc.
-   **¿Por qué es Peligroso en OT?**
    -   **Dispositivos Frágiles:** Un PLC o un dispositivo embebido no es un servidor robusto. Un escaneo de puertos puede ser interpretado como una avalancha de tráfico basura. El dispositivo puede no saber cómo manejar estos paquetes inesperados, causando que su pila de red se bloquee y el dispositivo se reinicie o deje de funcionar.
    -   **Impacto en la Disponibilidad:** Un reinicio de un PLC puede detener una línea de producción entera, causando pérdidas millonarias o condiciones inseguras.
    -   **El escaneo activo está estrictamente prohibido** en la mayoría de las redes de OT en producción.

### El Enfoque Correcto: Monitoreo Pasivo

-   **¿Qué es el Monitoreo Pasivo?** Consiste en "escuchar" el tráfico de la red sin enviar un solo paquete propio. Se coloca un sensor de red en un puerto SPAN (Switched Port Analyzer) o a través de un TAP (Test Access Point) en un switch de red. El sensor recibe una copia de todo el tráfico que pasa por ese punto.
-   **¿Cómo Funciona?**
    1.  El sensor captura todo el tráfico de forma invisible.
    2.  Analiza los paquetes para identificar qué dispositivos están hablando, qué protocolos están usando (Modbus, DNP3) y qué comandos están enviando.
    3.  Crea un **inventario de activos** y un **mapa de comunicaciones** de forma automática.
    4.  Establece una **línea base (baseline)** de lo que es el comportamiento "normal" de la red.
    5.  Alerta sobre cualquier desviación de esa línea base.

-   **¿Qué puede detectar el Monitoreo Pasivo?**
    -   **Nuevos Dispositivos:** Si un dispositivo desconocido se conecta a la red.
    -   **Nuevas Comunicaciones:** Si un PLC que normalmente solo habla con una HMI de repente intenta conectarse a internet.
    -   **Comandos Inusuales:** Si se envía un comando de "reprogramar" a un PLC fuera de una ventana de mantenimiento.
    -   **Escaneos o Tráfico Malicioso:** Puede detectar si un atacante ha logrado entrar y está intentando escanear la red.

**Herramientas:** `Nozomi Networks`, `Dragos`, `Claroty`, `SecurityOnion` (código abierto con capacidades de monitoreo pasivo).
