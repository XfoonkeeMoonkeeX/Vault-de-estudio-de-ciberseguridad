# Protocolos Comunes de OT

Los protocolos de Tecnología Operacional (OT) son a menudo antiguos, diseñados hace décadas cuando la seguridad no era una preocupación. Su principal objetivo era la fiabilidad y la velocidad, no la confidencialidad o la autenticación.

### Modbus

-   **¿Qué es?** Es el "abuelo" de los protocolos industriales, creado en 1979. Es, con diferencia, el protocolo más extendido en los sistemas de control industrial.
-   **Arquitectura:** Modelo **Maestro/Esclavo**.
    -   Un **Maestro** (ej. una HMI o un servidor SCADA) envía peticiones.
    -   Múltiples **Esclavos** (ej. PLCs) responden.
-   **Funcionamiento:** Se basa en leer y escribir valores en "registros" y "bobinas" (coils). Un maestro puede pedirle a un esclavo "dame el valor del registro de temperatura" o "activa la bobina del motor".
-   **Inseguridad por Diseño:**
    -   **Sin autenticación:** Cualquier dispositivo en la red puede enviar un comando Modbus a un esclavo, y este obedecerá. No hay forma de verificar quién envía la orden.
    -   **Sin cifrado:** Todos los comandos y respuestas viajan en texto plano. Un atacante puede leerlos y modificarlos fácilmente.
    -   **Sin comprobación de integridad:** Un atacante puede interceptar un comando y cambiar un valor (ej. cambiar la temperatura deseada de 25°C a 250°C) y el PLC no se dará cuenta.

### DNP3 (Distributed Network Protocol 3)

-   **¿Qué es?** Es un protocolo más moderno y complejo que Modbus, muy utilizado en empresas de servicios públicos (electricidad, agua) en Norteamérica.
-   **Arquitectura:** También es Maestro/Esclavo, pero más avanzado.
-   **Características Clave:**
    -   **Reporte por Excepción:** A diferencia de Modbus donde el maestro debe preguntar constantemente, en DNP3 un esclavo puede reportar un cambio de estado de forma proactiva.
    -   **Fragmentación de Mensajes:** Puede manejar mensajes más grandes.
-   **Seguridad:** DNP3 tiene una extensión llamada **"Secure Authentication"** que añade autenticación a los mensajes para verificar la identidad del remitente y la integridad del mensaje. Sin embargo, su adopción no es universal y muchos sistemas DNP3 todavía operan sin esta capa de seguridad.

> [!WARNING] El Legado Inseguro
> La existencia de estos protocolos es una de las razones por las que la segmentación de red (como la del Modelo Purdue) es tan absolutamente crítica en OT. Ya que los propios protocolos no son seguros, la única defensa es asegurarse de que nadie no autorizado pueda llegar a hablar con los dispositivos.
