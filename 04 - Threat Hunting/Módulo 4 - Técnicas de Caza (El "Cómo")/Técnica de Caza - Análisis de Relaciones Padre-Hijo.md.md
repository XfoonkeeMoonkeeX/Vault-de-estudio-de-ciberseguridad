# Técnica de Caza: Análisis de Relaciones Padre-Hijo de Procesos

> [!QUOTE] "Dime quién es tu padre y te diré si eres sospechoso."

En un sistema operativo, los procesos no aparecen de la nada. Casi siempre, un proceso es iniciado por otro proceso (su "padre"). Analizar esta relación genealógica es una de las técnicas de caza más efectivas para detectar comportamientos anómalos.

**Fuente de Datos Clave:** **Sysmon (Event ID 1)**, que registra explícitamente el nombre y el ID del proceso padre (`ParentProcess`) y del proceso hijo (`Process`).

### Relaciones Padre-Hijo Normales vs. Anómalas

Hay ciertas relaciones que son completamente normales y ocurren miles de veces al día:
-   `explorer.exe` (el escritorio de Windows) iniciando `chrome.exe` (cuando haces doble clic en el icono).
-   `svchost.exe` iniciando otros procesos de sistema como `services.exe`.

El objetivo del cazador es buscar relaciones que rompen la lógica esperada.

### Banderas Rojas (Relaciones Anómalas a Cazar)

-   **Un Proceso de Ofimática iniciando un Intérprete de Comandos:**
    -   **Relación:** `winword.exe` -> `cmd.exe`
    -   **Relación:** `excel.exe` -> `powershell.exe`
    -   **Relación:** `acrord32.exe` (Adobe Reader) -> `powershell.exe`
    -   **Significado:** Esta es una señal clásica de una explotación exitosa a través de un **documento con macros maliciosas**. El usuario abre un documento de Word, habilita las macros, y estas ejecutan un script de PowerShell para descargar la siguiente fase del ataque.

-   **Un Servidor Web iniciando un Intérprete de Comandos:**
    -   **Relación:** `w3wp.exe` (IIS de Windows) -> `cmd.exe`
    -   **Relación:** `httpd.exe` (Apache) -> `/bin/bash`
    -   **Significado:** Indica una explotación exitosa de una vulnerabilidad de **ejecución remota de comandos (RCE)** en la aplicación web. El atacante ha logrado que el servidor web ejecute un comando en el sistema operativo subyacente.

-   **Herramientas de Administración Remota iniciando Procesos Inusuales:**
    -   **Relación:** `PsExec.exe` -> `powershell.exe`
    -   **Significado:** `PsExec` es una herramienta legítima de Sysinternals para ejecutar comandos de forma remota. Los atacantes la aman para el **movimiento lateral**. Ver `PsExec` ejecutando comandos en múltiples máquinas de la red es una señal de que un atacante se está moviendo.

-   **Procesos del Sistema ejecutándose desde un Padre Inesperado:**
    -   **Relación:** `winword.exe` -> `svchost.exe`
    -   **Significado:** `svchost.exe` debería ser iniciado por `services.exe`. Si es iniciado por otro proceso, es muy probable que sea un malware disfrazado con un nombre legítimo.