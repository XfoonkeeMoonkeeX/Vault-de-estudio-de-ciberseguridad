# 🛠️ Actividad Práctica: Escribir Hipótesis de Caza Basadas en ATT&CK

> [!check] Objetivo
> Traducir tres técnicas del framework MITRE ATT&CK en hipótesis de caza específicas, accionables y comprobables. Para cada hipótesis, debes definir qué buscarías y en qué fuentes de datos.

Este ejercicio es el núcleo del trabajo de un Threat Hunter.

---

### Formato de la Hipótesis

Para cada una, sigue esta estructura:

-   **Técnica ATT&CK:** ID y Nombre.
-   **Hipótesis:** Una declaración clara de lo que supones que el atacante está haciendo.
-   **Fuentes de Datos Clave:** Los tipos de logs que necesitarías para investigar.
-   **Indicadores de Caza (Lo que buscarías):** Los patrones, comandos o anomalías específicos que buscarías en esos datos.

---

### Ejemplo de Hipótesis (el que ya conoces)

-   **Técnica ATT&CK:** `T1059.001: PowerShell`
-   **Hipótesis:** Un adversario podría estar usando PowerShell para descargar herramientas o malware desde internet de forma "sin fichero" (fileless).
-   **Fuentes de Datos Clave:**
    1.  Logs de Creación de Procesos (Sysmon ID 1).
    2.  Logs de Script Block de PowerShell (Event ID 4104).
    3.  Logs de Conexiones de Red (Sysmon ID 3).
-   **Indicadores de Caza:**
    -   Buscar en la línea de comandos de `powershell.exe` los parámetros `-nop`, `-w hidden`, `-enc` (que indica un comando codificado en Base64).
    -   Buscar en los logs de Script Block los comandos `IEX`, `Invoke-Expression`, `DownloadString`, `Invoke-WebRequest`.
    -   Correlacionar las conexiones de red del proceso PowerShell con dominios o IPs sospechosas.

---

### Tu Misión: Crea Tres Hipótesis Nuevas

**1. Hipótesis sobre Persistencia:**
-   **Técnica ATT&CK:** `T1547.001: Registry Run Keys / Startup Folder`
-   **Hipótesis:** *[Escribe aquí tu suposición sobre cómo un atacante usaría esta técnica]*
-   **Fuentes de Datos Clave:** *[Enumera los logs que necesitarías, ej. Sysmon, logs de registro]*
-   **Indicadores de Caza:** *[Describe qué buscarías: qué claves de registro monitorear, qué anomalías te harían sospechar]*

**2. Hipótesis sobre Evasión de Defensas:**
-   **Técnica ATT&CK:** `T1070.004: File Deletion`
-   **Hipótesis:** *[Escribe tu suposición: ¿por qué un atacante borraría sus herramientas?]*
-   **Fuentes de Datos Clave:** *[Enumera los logs que necesitarías]*
-   **Indicadores de Caza:** *[Describe qué buscarías: ¿qué comandos de borrado son sospechosos (`sdelete.exe`)? ¿En qué directorios? ¿Qué patrón de actividad te alertaría?]*

**3. Hipótesis sobre Acceso a Credenciales:**
-   **Técnica ATT&CK:** `T1003: OS Credential Dumping`
-   **Hipótesis:** *[Escribe tu suposición sobre cómo un atacante intentaría robar contraseñas de la memoria]*
-   **Fuentes de Datos Clave:** *[Enumera los logs que necesitarías. Piensa en acceso a procesos.]*
-   **Indicadores de Caza:** *[Describe qué buscarías: ¿qué proceso intentando acceder a la memoria de `lsass.exe` es una bandera roja gigante? ¿Qué herramientas conocidas (como `mimikatz`) podrías buscar por su nombre o hash?]*
