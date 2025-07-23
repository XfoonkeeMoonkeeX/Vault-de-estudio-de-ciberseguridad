# Tipos de Hipótesis de Caza

> [!QUOTE] "Una buena hipótesis no pregunta '¿Estamos comprometidos?', pregunta 'Si un atacante usara la técnica X, ¿qué artefactos específicos dejaría en mis logs?'"

Una hipótesis de caza es una suposición comprobable sobre la actividad del adversario en tu red. No todas las hipótesis nacen de la misma manera. Generalmente se dividen en tres categorías principales.

### 1. Hipótesis Basadas en Inteligencia (Intelligence-Driven)

-   **Definición:** Son las hipótesis de mayor fidelidad. Se basan en inteligencia de amenazas (Threat Intelligence) sobre las TTPs que están usando activamente los adversarios en el mundo real.
-   **Fuente:**
    -   Informes de compañías de ciberseguridad (Mandiant, CrowdStrike, etc.).
    -   Alertas de agencias gubernamentales (CISA, etc.).
    -   Blogs de investigadores de seguridad.
    -   Feeds de inteligencia de amenazas comerciales.
-   **Proceso:** Lees un informe que dice: "El grupo de ransomware `LockBit 3.0` está usando la herramienta legítima `AnyDesk` para el acceso remoto a las víctimas."
-   **Hipótesis Resultante:** "**Un atacante podría estar abusando de `AnyDesk.exe` para mantener persistencia y control remoto en nuestra red.** Voy a cazar ejecuciones de `AnyDesk.exe` desde ubicaciones inusuales o en máquinas donde no debería estar instalado (como servidores)."

### 2. Hipótesis Basadas en Anomalías (Anomaly-Driven)

-   **Definición:** Se basan en la búsqueda de comportamientos que se desvían de una línea base (baseline) de actividad "normal" conocida. Son menos específicas que las basadas en inteligencia.
-   **Fuente:** Tu propio conocimiento de la red y el uso de herramientas de visualización de datos para encontrar valores atípicos.
-   **Proceso:** Mientras analizas los logs, observas algo extraño: "El 99% de nuestros procesos de `svchost.exe` no tienen conexiones de red salientes, pero este en particular sí las tiene."
-   **Hipótesis Resultante:** "**Un proceso que se hace pasar por `svchost.exe` (o un `svchost.exe` legítimo comprometido) podría estar siendo usado como un canal de Comando y Control (C2).** Voy a investigar la reputación de la IP de destino y analizar la memoria de esa máquina para ver qué está haciendo realmente ese proceso."

### 3. Hipótesis Basadas en TTPs (ATT&CK-Driven)

-   **Definición:** Es el enfoque más estructurado y proactivo. Tomas una técnica directamente del framework **MITRE ATT&CK** y formulas una hipótesis sobre ella, independientemente de si tienes inteligencia específica que diga que está siendo usada contra ti.
-   **Fuente:** El framework MITRE ATT&CK.
-   **Proceso:** Eliges una técnica, por ejemplo, **`T1027: Obfuscated Files or Information`**.
-   **Hipótesis Resultante:** "**Un atacante podría estar usando scripts de PowerShell ofuscados para evadir la detección por firmas.** Voy a cazar en los logs de transcripción de PowerShell eventos que contengan un alto grado de caracteres especiales, codificación Base64 o comandos como `IEX` y `Invoke-Expression`, que a menudo se usan para ejecutar código ofuscado."

> [!check] Conclusión
> Un programa de Threat Hunting maduro utiliza una combinación de los tres tipos. Las hipótesis basadas en inteligencia son excelentes para cazar amenazas actuales y relevantes, mientras que las basadas en TTPs aseguran una cobertura de seguridad amplia y sistemática a lo largo del tiempo.