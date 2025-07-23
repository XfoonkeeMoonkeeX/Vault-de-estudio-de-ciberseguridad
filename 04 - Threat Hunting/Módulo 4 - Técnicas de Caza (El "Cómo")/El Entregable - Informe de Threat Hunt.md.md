### 3. El Entregable: Informe de Threat Hunt

Crea un informe claro y conciso. La calidad de la documentación es tan importante como la calidad de la caza. Usa el siguiente formato para cada una de tus tres cacerías.

---
> [!example] Estructura del Informe (Repetir para cada hipótesis)
>
> ## Cacería #1: Título Descriptivo
> *(Ej: Caza de Persistencia a través de Tareas Programadas)*
>
> ---
>
> ### 1. Hipótesis
> -   **Técnica ATT&CK Asociada:** (Ej: `T1053.005: Scheduled Task`)
> -   **Descripción de la Hipótesis:**
>     > "Parto de la suposición de que un adversario ha obtenido acceso inicial y ahora busca establecer persistencia en una máquina comprometida. Una de las técnicas más comunes para esto es la creación de una Tarea Programada que ejecute su malware periódicamente. Mi objetivo es buscar la creación de tareas programadas no estándar o sospechosas en el entorno."
>
> ### 2. Consulta y Metodología de Búsqueda
> -   **Plataforma Usada:** (Ej: Splunk Enterprise 9.0)
> -   **Consulta Exacta (SPL):**
>     ```splunk
>     index="mordor" sourcetype="xmlwineventlog" EventCode=4698
>     | stats count by host, TaskName, Author, CommandLine
>     | sort count asc
>     ```
> -   **Justificación de la Consulta:**
>     > "Esta consulta busca en el índice 'mordor' eventos de Windows con `EventCode=4698`, que corresponde a 'A scheduled task was created'. Luego, utilizo `stats` para apilar (stack) los resultados por nombre de la tarea, autor y el comando a ejecutar. Al ordenar por la cuenta en orden ascendente (`sort count asc`), las tareas más raras o únicas aparecerán primero, que son las más sospechosas."
>
> ### 3. Hallazgos
> -   **Resumen de los Hallazgos:**
>     > "La consulta devolvió 5 tareas creadas. Cuatro de ellas parecen ser legítimas y relacionadas con Google Chrome y Microsoft Office. Sin embargo, se identificó una tarea única llamada **'AtomicsRedTeam'** en el host **'WORKSTATION-1'**."
> -   **Evidencia Clave:** (Describe el resultado relevante de tu consulta)
>     -   **host:** `WORKSTATION-1`
>     -   **TaskName:** `AtomicsRedTeam`
>     -   **Author:** `WORKSTATION-1\Administrator`
>     -   **CommandLine:** `C:\Windows\System32\cmd.exe /c "powershell.exe -noni -nop -w hidden -c ... (comando ofuscado) ..."`
>     -   **(Opcional):** Incluye una captura de pantalla de los resultados en tu SIEM.
>
> ### 4. Conclusión de la Cacería
> -   **Veredicto:** (Malicioso, Benigno, o Sospechoso/Requiere más investigación).
>     > "La actividad es considerada **altamente maliciosa**."
> -   **Justificación de la Conclusión:**
>     > "La tarea tiene múltiples indicadores de malicia: 1) El nombre 'AtomicsRedTeam' sugiere una actividad de simulación de adversario. 2) El comando a ejecutar es una instancia de PowerShell ofuscada y oculta, lo cual no es un comportamiento normal para una tarea legítima. 3) Esta tarea es única en todo el dataset."
> -   **Siguientes Pasos Recomendados:**
>     > "Se recomienda iniciar un proceso de Respuesta a Incidentes para la máquina 'WORKSTATION-1'. El siguiente paso inmediato sería analizar el contenido del comando de PowerShell ofuscado para entender su funcionalidad y buscar los IoCs asociados (IPs, dominios, hashes) en el resto de la red."
>
> ---
> *(Aquí empezarías la Cacería #2 con una nueva hipótesis)*

---

### Hipótesis Sugeridas para tus Otras Cacerías

Para inspirarte, aquí tienes algunas ideas:
-   **Acceso a Credenciales:** Caza de procesos accediendo a la memoria de `lsass.exe` (ATT&CK `T1003`).
-   **Evasión de Defensas:** Caza de comandos que intentan deshabilitar Windows Defender usando `Set-MpPreference` en PowerShell (ATT&CK `T1562.001`).
-   **Ejecución:** Caza de ejecuciones de `rundll32.exe` que llaman a funciones en DLLs ubicadas en directorios no estándar como `C:\Users\Public\` (ATT&CK `T1218.011`).
-   **Comando y Control:** Caza de consultas DNS a dominios con alta entropía o con extensiones de dominio raras (`.xyz`, `.top`, etc.) (ATT&CK `T1568.002`).
```