
### 2. El Entregable: Informe de Evaluación de Riesgos

Tu informe debe ser un documento profesional y estructurado. A continuación se detalla cada sección.

> [!example] Estructura del Informe de Evaluación de Riesgos
>
> **a. Descripción del Sistema y Alcance de la Evaluación**
> -   **Sistema Elegido:** (Ej. "Sistema de Riego Inteligente para una Finca de 10 Hectáreas").
> -   **Descripción:** Explica brevemente cómo funciona el sistema, su propósito y los resultados deseados (ej. "optimizar el uso del agua y maximizar la cosecha").
>
> **b. Sección 1: Identificación de Activos Críticos**
> -   Enumera los componentes clave del sistema, tanto físicos como digitales. Piensa en términos del Modelo Purdue.
>   -   **Activos Físicos/OT:** Sensores de humedad, bombas de agua, válvulas, PLCs.
>   -   **Activos de Red:** Switches de red industrial, firewalls, red Wi-Fi/celular para la comunicación.
>   -   **Activos de IT/Nube:** Servidor de historial, plataforma en la nube para la gestión, aplicación móvil del agricultor.
> -   **Justificación:** Para cada activo, explica brevemente por qué es crítico. (Ej. "El PLC de la bomba principal es crítico porque su fallo detiene todo el riego").
>
> **c. Sección 2: Análisis de Amenazas y Vulnerabilidades**
> -   Aquí es donde te pones el sombrero de atacante. Para cada activo crítico, identifica posibles amenazas.
>   -   **Amenaza:** ¿*Qué* podría pasar? (Ej. "Un atacante toma control del PLC de la bomba").
>   -   **Vulnerabilidad:** ¿*Cómo* podría pasar? (Ej. "El PLC usa el protocolo Modbus sin autenticación y está en una red Wi-Fi con una contraseña débil").
> -   **Ejemplos de Amenazas/Vulnerabilidades a considerar:**
>     -   **PLC:** Acceso no autorizado vía Modbus, denegación de servicio por escaneo activo, modificación del firmware.
>     -   **HMI/Plataforma en la Nube:** Credenciales por defecto, vulnerabilidades web (OWASP Top 10), falta de cifrado en la comunicación.
>     -   **Red:** Interceptación de tráfico (Man-in-the-Middle), spoofing de paquetes, jamming de la señal inalámbrica.
>
> **d. Sección 3: Evaluación del Impacto Potencial**
> -   Para cada amenaza identificada, evalúa las consecuencias si el ataque tuviera éxito. Piensa más allá del impacto financiero.
>   -   **Impacto Operacional:** ¿Se detiene la operación? ¿Se daña el equipo? (Ej. "La denegación de servicio en los sensores de humedad podría llevar a un riego excesivo, ahogando los cultivos").
>   -   **Impacto Financiero:** ¿Cuánto dinero se pierde por la interrupción, el daño al equipo o la pérdida de producto? (Ej. "La pérdida de una cosecha completa").
>   -   **Impacto en la Seguridad Física (Salud y Seguridad Humana - HS&E):** ¿Podría alguien resultar herido? (En el caso del riego, el riesgo es bajo. En el caso de una planta química, sería altísimo).
>
> **e. Sección 4: Recomendaciones de Controles de Seguridad**
> -   Esta es la sección de soluciones. Para cada amenaza/vulnerabilidad, propón controles específicos para mitigar el riesgo. Basa tus recomendaciones en el estándar **ISA/IEC 62443**.
>   -   **Controles Técnicos:**
>       -   **Segmentación de Red:** "Implementar un firewall industrial para crear una Zona de Control que aísle los PLCs del resto de la red, siguiendo el Modelo Purdue." (Referencia a Zonas y Conductos de IEC 62443).
>       -   **Monitoreo de Red:** "Desplegar un sistema de monitoreo pasivo para establecer una línea base del tráfico Modbus y alertar sobre cualquier comando o comunicación anómala." (Referencia al requisito FR5 - Flujo de Datos Restringido y FR6 - Respuesta Oportuna).
>       -   **Control de Acceso:** "Asegurar la plataforma en la nube con autenticación de dos factores (2FA) para todos los usuarios administradores." (Referencia al requisito FR1 - Control de Acceso).
>   -   **Controles de Procedimiento (Personas y Procesos):**
>       -   "Crear una política de gestión de contraseñas que exija cambiar todas las credenciales por defecto de los dispositivos."
>       -   "Establecer un programa de gestión de parches para la plataforma de gestión y los sistemas operativos, definiendo ventanas de mantenimiento que minimicen el impacto operacional."
>       -   "Limitar el acceso físico a los gabinetes de control donde se encuentran los PLCs."
```
