# 🛠️ Actividad Práctica: Explorar Datasets Públicos de Ataques

> [!check] Objetivo
> El mayor desafío para un cazador que está aprendiendo es tener acceso a datos realistas para practicar. Afortunadamente, la comunidad de ciberseguridad ha creado y compartido datasets masivos que contienen los logs de ataques simulados, permitiéndonos cazar sin riesgo.

### 1. Elige tu Dataset

-   **Mordor (Recomendado):**
    -   **¿Qué es?** Es un proyecto liderado por Roberto Rodriguez (@Cyb3rWard0g) que tiene como objetivo proporcionar datasets pre-grabados de técnicas de adversarios basadas en MITRE ATT&CK.
    -   **Sitio Web:** [https://mordordatasets.com/](https://mordordatasets.com/)
    -   **Ventaja:** Cada dataset está enfocado en una o varias técnicas de ATT&CK específicas. Vienen en formato de logs de Windows (EVTX) y a menudo incluyen una importación lista para Splunk o ELK.

-   **Security Datasets Project (Splunk):**
    -   **¿Qué es?** Es un proyecto de Splunk que alberga varios datasets de conferencias de seguridad como "Boss of the SOC" (BOTS).
    -   **Sitio Web:** [https://github.com/splunk/security_datasets](https://github.com/splunk/security_datasets)
    -   **Ventaja:** Son datasets enormes y muy realistas, perfectos para practicar con Splunk.

### 2. Tu Misión

1.  **Navega a Mordor.** Ve a la sección de "Scenarios".
2.  **Elige un escenario.** Un buen punto de partida es el escenario de `APT29`, que simula las acciones de este conocido grupo adversario.
3.  **Descarga los datos.** Verás enlaces para descargar los archivos de logs en formato `EVTX`. Descarga algunos de ellos.
4.  **Analiza los logs localmente (Método Básico):**
    -   En una VM de Windows, puedes abrir los archivos `.evtx` directamente con el **Visor de Eventos**.
    -   Selecciona "Action" -> "Open Saved Log..." y elige el archivo que descargaste.
    -   Ahora puedes filtrar y buscar dentro de esos logs como si fueran los de un sistema real.
5.  **Aplica las técnicas de caza:**
    -   Basado en la descripción del escenario en la web de Mordor (que te dice qué técnicas se simularon), intenta encontrar la evidencia tú mismo.
    -   Por ejemplo, si el escenario incluyó la técnica `T1059.001: PowerShell`, filtra los logs de PowerShell y busca los comandos sospechosos.
    -   Si incluyó `T1053.005: Scheduled Task`, busca el Event ID `4698` para ver la creación de la tarea.

Esta actividad te permite aplicar las técnicas de caza en un entorno seguro y realista, pasando de la teoría a la práctica de análisis de logs.
