# 🏆 Proyecto Final: Resolver un Reto Completo de DFIR

---

> [!check] Objetivo Final
> Este proyecto es la culminación de todo el ramo. Tu misión es actuar como un analista de Respuesta a Incidentes y Forense Digital (DFIR) en un escenario realista. Deberás investigar un conjunto de evidencias (imagen de disco, volcado de memoria, captura de red, logs) para reconstruir un incidente de seguridad de principio a fin y presentar tus hallazgos en un informe profesional.

### 1. Elige tu Plataforma de Desafío

Estas plataformas ofrecen retos de alta calidad, a menudo basados en incidentes reales, que proporcionan todas las evidencias que necesitas.

-   **CyberDefenders:** [https://cyberdefenders.org/](https://cyberdefenders.org/)
    -   Es una de las mejores y más populares. Ofrece una gran cantidad de retos ("labs") gratuitos de diferentes categorías (forense, respuesta a incidentes, malware). Los retos suelen incluir una historia y un conjunto de preguntas que te guían en la investigación.
-   **Blue Teams Academy:** [https://blueteams.academy/](https://blueteams.academy/)
    -   Otra excelente plataforma centrada en el lado defensivo de la ciberseguridad. Ofrece laboratorios y retos que cubren forense, análisis de logs y más.

**Recomendación:** Comienza con un reto de nivel "Fácil" o "Medio" en CyberDefenders. Retos como **"Boss of the SOC" (BOTS)** o **"Tangled"** son excelentes puntos de partida.

### 2. El Proceso de Investigación

Una vez que descargues los archivos del reto, sigue la metodología que hemos aprendido a lo largo de los módulos:

1.  **Análisis de Disco (Autopsy):** Carga la imagen de disco. Realiza una primera pasada: busca archivos sospechosos, revisa la actividad del usuario en el timeline, busca palabras clave relevantes para el escenario y extrae artefactos del sistema operativo.
2.  **Análisis de Memoria (Volatility):** Carga el volcado de memoria. Identifica procesos maliciosos, conexiones de red ocultas, comandos ejecutados por el atacante y cualquier otra evidencia volátil. A menudo, la memoria te dará el "momento exacto" del compromiso.
3.  **Análisis de Red (Wireshark):** Abre el archivo PCAP. Filtra el tráfico para identificar la comunicación del atacante. Reconstruye sesiones para ver qué datos se exfiltraron o qué comandos se enviaron. Correlaciona las IPs y puertos que encuentres aquí con las conexiones que viste en Volatility.
4.  **Análisis de Logs (grep, awk, sed):** Revisa los archivos de log proporcionados. Busca en los logs del firewall, servidor web y sistema operativo para encontrar las huellas del atacante y corroborar los hallazgos de tus otros análisis.

> [!TIP] Correlación
> La clave de un buen análisis es **correlacionar la evidencia**. Si encuentras una conexión a una IP maliciosa en Wireshark, debes buscar qué proceso generó esa conexión en Volatility y qué acciones realizó ese proceso en los logs del sistema y en el timeline de Autopsy.

---

### 3. El Entregable: Informe Forense Profesional

Tu trabajo no termina al encontrar las respuestas. Debes ser capaz de comunicarlas de forma clara y profesional. Tu informe debe tener la siguiente estructura:

> [!example] Estructura del Informe Forense
>
> **1. Resumen Ejecutivo (Executive Summary)**
> -   **Audiencia:** Gerencia, C-level (no técnicos).
> -   **Contenido:** Un párrafo corto y directo. ¿Qué pasó? ¿Cuál fue el impacto? ¿Qué se necesita hacer? Sin jerga técnica.
>     -   *Ejemplo: "Entre el 10 y el 12 de mayo, un atacante externo comprometió el servidor web de la compañía explotando una vulnerabilidad conocida. El atacante exfiltró una base de datos de clientes antes de que el sistema fuera contenido. Se recomienda aplicar parches de inmediato y realizar una auditoría de contraseñas."*
>
> **2. Cronología Detallada del Ataque (Timeline)**
> -   **Audiencia:** Equipo técnico.
> -   **Contenido:** Una lista con marca de tiempo (timestamp) de cada evento clave del ataque, en orden cronológico.
>     -   `2023-10-26 14:30 UTC` - El atacante realiza un escaneo de puertos desde la IP `X.X.X.X`.
>     -   `2023-10-26 14:35 UTC` - Explotación exitosa de la vulnerabilidad `CVE-XXXX-XXXX` en el servidor web.
>     -   `2023-10-26 14:37 UTC` - El malware `malicioso.exe` es descargado y ejecutado.
>     -   `2023-10-26 15:00 UTC` - Conexión de C2 establecida con la IP `Y.Y.Y.Y` en el puerto 4444.
>     -   ... y así sucesivamente.
>
> **3. Evidencia Encontrada (Análisis Detallado)**
> -   **Audiencia:** Equipo técnico forense.
> -   **Contenido:** Esta es la sección más larga. Para cada paso del timeline, presenta la evidencia que lo respalda. Incluye capturas de pantalla de tus herramientas (Autopsy, Volatility, Wireshark), fragmentos de logs relevantes y tu explicación de por qué esa evidencia prueba ese punto.
>
> **4. Indicadores de Compromiso (IoCs)**
> -   **Audiencia:** Equipo de seguridad (SOC), administradores de sistemas.
> -   **Contenido:** Una lista clara y procesable de IoCs que pueden ser usados para buscar al atacante en otros sistemas y para mejorar las defensas.
>     -   **Hashes de Archivos (MD5, SHA1, SHA256):** `malicioso.exe`, etc.
>     -   **Direcciones IP:** IP del atacante, IPs de los servidores C2.
>     -   **Dominios:** Dominios usados por el malware.
>     -   **Artefactos en el Host:** Nombres de archivos o claves de registro creadas por el malware para persistencia.
>
> **5. Recomendaciones**
> -   **Audiencia:** Gerencia y equipo técnico.
> -   **Contenido:** Un conjunto de acciones específicas para remediar el incidente y prevenir que vuelva a ocurrir. Divídelas en corto, mediano y largo plazo.
>     -   **Corto Plazo (Remediación):** Aislar las máquinas afectadas, bloquear IPs/dominios en el firewall, cambiar todas las contraseñas.
>     -   **Mediano Plazo (Endurecimiento):** Aplicar los parches de seguridad faltantes, implementar segmentación de red.
>     -   **Largo Plazo (Estrategia):** Implementar un programa de gestión de vulnerabilidades, realizar capacitaciones de seguridad para el personal.

Este proyecto te dará una experiencia increíblemente valiosa y un entregable tangible que podrás usar para demostrar tus habilidades en futuras entrevistas de trabajo. ¡Mucha suerte!