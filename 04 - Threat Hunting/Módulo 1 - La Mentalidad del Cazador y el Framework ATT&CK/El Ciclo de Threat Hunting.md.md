# El Ciclo de Threat Hunting

> [!QUOTE] "El Threat Hunting no es una búsqueda aleatoria; es un proceso disciplinado y repetible, similar al método científico."

El Threat Hunting sigue un ciclo estructurado para asegurar que las búsquedas sean eficientes y los resultados sean consistentes.

### Las Fases del Ciclo

1.  **Hipótesis (Hypothesis)**
    -   **¿Qué es?** Es el punto de partida. El Hunter formula una suposición educada sobre una posible actividad maliciosa que podría estar ocurriendo en la red. Una buena hipótesis es específica y comprobable.
    -   **Fuentes de Hipótesis:**
        -   **Inteligencia de Amenazas (Threat Intelligence):** "Un informe reciente dice que el grupo APT29 está usando la técnica X. ¿Podríamos estar siendo víctimas de esa técnica?".
        -   **Análisis del Entorno (Crown Jewels Analysis):** "¿Cuáles son nuestros activos más valiosos? ¿Cómo intentaría un atacante llegar a ellos? Hipótesis: 'Un atacante intentará acceder a nuestro servidor de base de datos de clientes desde la estación de trabajo de un desarrollador'".
        -   **Análisis de Anomalías:** "He notado un pico inusual de tráfico DNS hacia un dominio desconocido. Hipótesis: 'Podría ser un canal de Comando y Control (C2)'".
    -   **Ejemplo de Hipótesis:** "Un atacante está usando PowerShell para descargar y ejecutar código malicioso en memoria sin tocar el disco (`fileless malware`)."

2.  **Investigación (Investigation)**
    -   **¿Qué es?** La fase de recolección y análisis de datos para probar o refutar la hipótesis.
    -   **Proceso:** El Hunter utiliza diversas herramientas para buscar la evidencia. Para la hipótesis del ejemplo anterior:
        -   Buscar en los logs del SIEM y del EDR eventos de ejecución de `powershell.exe`.
        -   Analizar los logs de transcripción de PowerShell en busca de comandos sospechosos (`IEX (New-Object Net.WebClient).DownloadString(...)`).
        -   Examinar las conexiones de red salientes desde los procesos de PowerShell.

3.  **Descubrimiento (Uncovering)**
    -   **¿Qué es?** Analizar los resultados de la investigación para encontrar patrones maliciosos o TTPs (Tácticas, Técnicas y Procedimientos) de un adversario.
    -   **Resultado:** Si la hipótesis se confirma, se ha descubierto a un atacante. Se documentan los hallazgos: máquinas afectadas, cuentas comprometidas, herramientas del atacante, etc. Este descubrimiento desencadena formalmente un proceso de **Respuesta a Incidentes (IR)**.

4.  **Informe y Automatización (Informing & Automating)**
    -   **¿Qué es?** Es la fase de mejora continua. El conocimiento adquirido durante la caza se utiliza para fortalecer las defensas.
    -   **Proceso:**
        -   **Informe:** Se documentan los nuevos TTPs descubiertos y se comparten con el resto del equipo de seguridad.
        -   **Automatización:** Lo más importante. Se crean **nuevas reglas de detección** en el SIEM o el EDR para que, la próxima vez que el atacante use esta misma técnica, **se genere una alerta automáticamente**.
        -   El objetivo final del Threat Hunting es automatizarse a sí mismo. Cada caza exitosa debe convertir una amenaza desconocida en una conocida, moviéndola del dominio del "Threat Hunting Proactivo" al de la "Detección Reactiva".