# Técnica de Caza: Análisis de la Línea de Comandos

> [!QUOTE] "La línea de comandos no miente. Es el registro literal de la intención de quien la ejecutó."

Los adversarios modernos abusan constantemente de herramientas legítimas del sistema operativo (`powershell.exe`, `cmd.exe`, `wmic.exe`, `schtasks.exe`). Ya que el nombre del proceso es legítimo, la única forma de detectar su uso malicioso es analizando **qué argumentos** se le pasaron.

Gracias a fuentes de datos como **Sysmon (Event ID 1)**, tenemos acceso a esta información.

### Indicadores de Malicia en la Línea de Comandos

-   **Ofuscación:**
    -   Los atacantes ofuscan sus comandos para evadir la detección por firmas. Hay que buscar patrones de ofuscación.
    -   **Ejemplos en PowerShell:**
        -   Uso de acentos graves (`` ` ``) o concatenación de strings (`"po" + "wer" + "shell"`).
        -   Comandos codificados en **Base64** (buscar el flag `-e`, `-enc`, o `-EncodedCommand`).
        -   Uso de `IEX` (`Invoke-Expression`) para ejecutar comandos construidos en memoria.

-   **Abuso de Herramientas Legítimas:**
    -   **PowerShell:**
        -   `DownloadString` o `Invoke-WebRequest`: Para descargar archivos o herramientas desde internet.
        -   `-nop` (NoProfile), `-w hidden` (WindowStyle Hidden): Para ejecutar PowerShell de forma sigilosa, sin cargar perfiles y sin ventana visible.
    -   **Rundll32.exe:**
        -   Una herramienta legítima para ejecutar funciones desde DLLs. Los atacantes la usan para ejecutar código malicioso directamente desde una DLL sin un ejecutable principal. Una ejecución de `rundll32.exe` que llama a una DLL en una carpeta temporal o extraña es muy sospechosa.
    -   **WMIC.exe (Windows Management Instrumentation):**
        -   Permite realizar tareas administrativas. Los atacantes lo usan para el movimiento lateral (`/node:REMOTEMACHINE process call create "malware.exe"`) o para obtener información del sistema.

-   **Redirección y Piping:**
    -   El uso de `>` para redirigir la salida de un comando a un archivo (ej. `ipconfig /all > C:\Users\Public\network_info.txt`) puede ser una técnica de reconocimiento.
    -   El uso de `|` para encadenar comandos.

### Cómo Cazarlo

1.  **Recolectar los logs:** Asegúrate de que Sysmon o tu EDR estén capturando los argumentos de la línea de comandos.
2.  **Filtrar por procesos de interés:** Enfoca tu caza en procesos que son frecuentemente abusados (`powershell.exe`, `cmd.exe`, `wmic.exe`, `cscript.exe`, `mshta.exe`).
3.  **Buscar palabras clave y patrones:** Usa tu SIEM para buscar las palabras clave mencionadas arriba (`IEX`, `-enc`, `DownloadString`, etc.).
4.  **"Stacking":** Aplica la técnica de "stacking" a los argumentos de la línea de comandos para encontrar los más raros.