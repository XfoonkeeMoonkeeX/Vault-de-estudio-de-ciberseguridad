# IT vs. OT vs. IoT: Un Choque de Prioridades

> [!QUOTE] "En IT, si el servidor de correo se cae, la gente se enfada. En OT, si el controlador de la turbina se cae, la ciudad se queda a oscuras."

Para entender la seguridad en estos dominios, primero hay que entender sus diferencias fundamentales y, sobre todo, sus prioridades.

### IT (Information Technology)
-   **Definición:** La tecnología de la información tradicional. Son los sistemas que gestionan datos: servidores, redes corporativas, bases de datos, aplicaciones empresariales, etc.
-   **Prioridades (Tríada CIA):**
    1.  **Confidencialidad:** Proteger los datos contra el acceso no autorizado es lo más importante.
    2.  **Integridad:** Asegurar que los datos sean precisos y no hayan sido manipulados.
    3.  **Disponibilidad:** Asegurar que los sistemas y datos estén disponibles para los usuarios.

### OT (Operational Technology)
-   **Definición:** La tecnología operacional. Son los sistemas de hardware y software que monitorizan y controlan procesos físicos, dispositivos e infraestructura. Hablamos de Sistemas de Control Industrial (ICS), SCADA, PLCs, etc.
-   **Prioridades (La Tríada CIA Invertida):**
    1.  **Disponibilidad:** ¡Lo más importante! Un sistema de control industrial (ej. una red eléctrica, una planta de tratamiento de agua) NO PUEDE PARAR. Una interrupción, aunque sea de segundos, puede tener consecuencias catastróficas, costosas y peligrosas para la seguridad física.
    2.  **Integridad:** Los datos que controlan los procesos deben ser exactos. Un valor incorrecto de temperatura o presión enviado a un PLC puede causar una explosión.
    3.  **Confidencialidad:** Es la menor de las preocupaciones. A menudo, los datos de los procesos no son sensibles. Es más importante que el sistema funcione a que sus datos operativos sean secretos.

### IoT (Internet of Things)
-   **Definición:** El Internet de las Cosas. Son dispositivos físicos embebidos con sensores, software y otras tecnologías que se conectan e intercambian datos con otros dispositivos y sistemas a través de internet. Es un puente entre el mundo físico y el digital.
-   **Prioridades:** Es un híbrido y depende del dispositivo.
    -   **Para un Smart TV (IoT de consumo):** La disponibilidad (que funcione) es clave.
    -   **Para un marcapasos conectado (IoT Médico):** La integridad (que los datos sean correctos) y la disponibilidad son vitales.
    -   **Para una cámara de seguridad (IoT de Vigilancia):** La confidencialidad (que nadie más vea el video) es muy importante.

> [!WARNING] Implicaciones de Seguridad
> Esta diferencia de prioridades lo cambia todo. No puedes simplemente aplicar las mismas soluciones de seguridad de IT (como un parche que requiere reiniciar un sistema) a un entorno de OT, porque la **disponibilidad es la reina**.
