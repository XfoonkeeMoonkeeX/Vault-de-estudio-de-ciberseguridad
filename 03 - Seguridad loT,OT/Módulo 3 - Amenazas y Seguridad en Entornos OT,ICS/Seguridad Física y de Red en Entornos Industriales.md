# Seguridad Física y de Red en Entornos Industriales

> [!QUOTE] "En OT, un firewall es tan importante como una valla con alambre de espino. La seguridad digital y la física son dos caras de la misma moneda."

Dado que los protocolos de OT son inherentemente inseguros, las defensas de red y físicas son la principal línea de protección.

### Segmentación de Red (El Modelo Purdue en la Práctica)

-   **Concepto:** Es la defensa más fundamental. Consiste en dividir la gran red plana en múltiples sub-redes o "zonas" más pequeñas y aisladas, y controlar estrictamente el tráfico que puede pasar entre ellas.
-   **Implementación:**
    -   Se utilizan **firewalls** para crear barreras entre los niveles del Modelo Purdue.
    -   El objetivo es crear "conductos" de comunicación estrictamente definidos. Por ejemplo, solo permitir que el servidor HMI del Nivel 2 se comunique con un PLC específico del Nivel 1 usando el protocolo Modbus en el puerto 502, y bloquear todo lo demás.
    -   Esto previene que un atacante que compromete la red de IT (Nivel 5) pueda moverse lateralmente y llegar directamente a los PLCs (Nivel 1).

### Firewalls Industriales

-   **Diferencia con Firewalls de IT:** Los firewalls industriales están diseñados para operar en entornos hostiles y, lo más importante, tienen capacidades de **Inspección Profunda de Paquetes (DPI)** para protocolos industriales.
-   **Inspección Profunda de Paquetes (DPI):** Un firewall normal puede bloquear o permitir el tráfico en el puerto 502 (Modbus). Un firewall industrial con DPI puede mirar *dentro* del paquete Modbus y aplicar reglas más granulares, como: "Permitir comandos de *lectura* de Modbus, pero bloquear comandos de *escritura* de Modbus", proporcionando una capa de seguridad mucho más fuerte.

### Diodos de Datos (Data Diodes)

-   **¿Qué es?** Es un dispositivo de seguridad de hardware que se sitúa entre dos redes y permite que los datos fluyan **en una sola dirección**. Es una calle de un solo sentido a nivel físico (basada en fibra óptica).
-   **Caso de Uso:** Son la forma más segura de segmentar una red. Se usan a menudo para proteger las redes más críticas (como la red de control de una central nuclear) del resto del mundo.
-   **Ejemplo:** Puedes colocar un diodo de datos para permitir que los datos de los sensores fluyan *desde* la red de OT *hacia* la red de IT (para que los analistas de negocio puedan verlos), pero hace físicamente imposible que cualquier tráfico o ataque fluya *desde* la red de IT *hacia* la red de OT. Garantiza un aislamiento total en una dirección.

### Seguridad Física

-   **Importancia:** No se debe subestimar. Si un atacante puede acceder físicamente a un PLC o a un puerto de red en la planta, muchas de las defensas de red se vuelven inútiles.
-   **Medidas:**
    -   Control de acceso con tarjetas.
    -   Cámaras de vigilancia.
    -   Gabinetes cerrados con llave para los equipos de control.
    -   Deshabilitación de puertos USB en los equipos críticos.
