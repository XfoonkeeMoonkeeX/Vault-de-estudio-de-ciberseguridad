# 🛠️ Herramienta a Dominar: El Framework MITRE ATT&CK®

> [!tool] ¿Qué es?
> MITRE ATT&CK® no es un software. Es una base de conocimiento globalmente accesible y una matriz curada de las Tácticas, Técnicas y Procedimientos (TTPs) de los adversarios, basada en observaciones del mundo real. Es el lenguaje universal que usan los defensores, los equipos rojos y los proveedores de ciberseguridad para hablar sobre el comportamiento del adversario.

**Sitio Web:** [https://attack.mitre.org/](https://attack.mitre.org/)

### ¿Cómo está Estructurado?

ATT&CK se presenta como una **matriz**.
-   **Las Columnas son las Tácticas:** Representan las fases o el objetivo de un ataque, desde el reconocimiento inicial hasta el impacto final. Ejemplos: `Initial Access`, `Execution`, `Persistence`, `Defense Evasion`, `Exfiltration`, `Command and Control`.
-   **Las Celdas son las Técnicas:** Dentro de cada táctica, hay una lista de técnicas conocidas que los adversarios usan para lograr ese objetivo. Cada técnica tiene un ID único (ej. T1053).
-   **Sub-técnicas:** Algunas técnicas son muy amplias y se desglosan en sub-técnicas más específicas (ej. T1053.005 para Tareas Programadas de Windows).

### ¿Cómo se Usa en Threat Hunting?

ATT&CK es el mapa que guía la creación de hipótesis.

1.  **Selección de una Técnica (Formulación de la Hipótesis):**
    -   Un cazador no dice "¿qué busco hoy?". Dice: "Hoy voy a cazar la técnica **T1053: Scheduled Task/Job**". Esta es su hipótesis: "Un atacante podría estar usando tareas programadas para lograr persistencia en mi red".

2.  **Estudio de la Técnica:**
    -   El cazador va a la página de ATT&CK para la técnica T1053.
    -   **Lee la descripción:** Entiende cómo funciona la técnica.
    -   **Revisa los "Procedure Examples":** Ve qué grupos de atacantes (como APT29, FIN7) han usado esta técnica y cómo la implementaron.
    -   **Revisa las "Data Sources" y "Detection":** **¡Esta es la sección más importante para el hunting!** MITRE te dice exactamente qué logs y artefactos necesitas para detectar esta técnica. Para T1053, te dirá que necesitas:
        -   Logs de creación de procesos (para ver `schtasks.exe`).
        -   Logs de eventos de Windows (específicamente, ID 4698: "A scheduled task was created").
        -   Monitorización de archivos (para ver la creación de archivos de tareas en `C:\Windows\System32\Tasks`).

3.  **Ejecución de la Caza:**
    -   Con esa información, el cazador va a sus herramientas (SIEM, EDR) y construye consultas para buscar específicamente esos artefactos.
    -   *Ejemplo de consulta en un SIEM:* `SELECT * FROM windows_event_logs WHERE event_id = 4698 AND task_name NOT IN (lista_de_tareas_conocidas_y_legítimas)`.

### Tu Misión con ATT&CK
1.  Navega a la matriz de **ATT&CK for Enterprise**.
2.  Elige una **Táctica** que te interese, por ejemplo, `Persistence`.
3.  Elige una **Técnica** dentro de esa táctica. Por ejemplo: **`T1547: Boot or Logon Autostart Execution`**.
4.  Haz clic en ella y estudia la página a fondo.
5.  Concéntrate en la sección **"Detection"**. ¿Qué fuentes de datos (Data Sources) necesitas para detectar esta técnica? ¿Qué te sugiere MITRE que busques?
6.  En una nota de Obsidian, resume tus hallazgos. Documenta qué logs buscarías y qué anomalías te harían sospechar para cazar esa técnica específica.
