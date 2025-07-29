# Ruta de Aprendizaje: Threat Hunting (Caza de Amenazas)

## Introducción
Mientras el SOC (Centro de Operaciones de Seguridad) reacciona a las alertas, el Threat Hunter busca proactivamente lo que las alarmas no detectaron. Se parte de la hipótesis de que el atacante ya está dentro de la red. El lema aquí es: **"No esperes la alarma, busca al ladrón"**.

---

### Módulo 1: La Mentalidad del Cazador y el Framework ATT&CK
[[Mentalidad del Cazador.md]]
- [ ] **Tema:** Threat Hunting proactivo vs. Detección reactiva.
- [[Threat Hunting Proactivo vs Detección Reactiva.md]] 
- [ ] **Tema:** El ciclo de Threat Hunting: Hipótesis -> Investigación -> Descubrimiento -> Informe/Automatización.
- [[El Ciclo de Threat Hunting.md]]] ] 
- [ ] **Tema:** Dejar de pensar en IoCs (hashes, IPs) y empezar a pensar en TTPs (Tácticas, Técnicas y Procedimientos).
- [[Pensar en TTPs, no solo en IoCs.md]]
- [ ] **Herramienta a Dominar:** El framework `MITRE ATT&CK`. No es una herramienta, es un mapa del comportamiento del adversario. Elige una técnica (ej. "T1053: Scheduled Task/Job") y estúdiala a fondo.
- [[Herramienta a Dominar - MITRE ATT&CK.md]] 

### Módulo 2: Las Fuentes de Datos del Cazador
[[Fuentes de Datos del Cazador.md]]
- [ ] **Tema:** La telemetría es el terreno de caza. Fuentes de datos cruciales:
    - **Endpoint:** Logs de procesos, registros de Windows, PowerShell, Sysmon.
    - **Red:** Logs de Firewall/Proxy, DNS, Netflow, PCAP.
    - **Identidad:** Logs de autenticación (Active Directory, VPN).
    - [[La Telemetría como Terreno de Caza.md]]
- [ ] **Herramienta a Dominar:** `Sysmon`. Instalarlo y configurarlo en una VM de Windows. Generar actividad (abrir programas, ejecutar comandos) y ver la riqueza de los logs que genera en el Visor de Eventos.
    - [[Herramienta a Dominar - Sysmon.md]]

### Módulo 3: Formulando Hipótesis de Caza
[[Tipos de Hipótesis de Caza.md]]
- [ ] **Tema:** Tipos de hipótesis: basadas en inteligencia (un nuevo malware usa `X` técnica), basadas en anomalías (busquemos procesos con nombres extraños), etc.
- [[Tipos de Hipótesis de Caza.md]]
- [ ] **Actividad:** Escribir 3 hipótesis de caza basadas en técnicas de MITRE ATT&CK.
    - **Ejemplo:** "Un adversario podría estar usando PowerShell para descargar herramientas desde internet. Cazaré eventos de PowerShell que contengan las palabras `DownloadString` o `Invoke-WebRequest`."
    - [[Actividad - Escribir Hipótesis de Caza Basadas en ATT&CK.md]]

### Módulo 4: Técnicas de Caza (El "Cómo")
[[Técnicas de Caza.md]]
- [ ] **Tema:** "Stacking" o apilamiento: encontrar lo anómalo contando la frecuencia de eventos. (Ej. "stackear" todos los nombres de procesos y ver cuáles son los menos comunes).
- [[Técnica de Caza - Stacking.md]]
- [ ] **Tema:** Análisis de la línea de comandos: buscar ofuscación, comandos extraños o argumentos sospechosos.
- [[Técnica de Caza - Análisis de la Línea de Comandos.md]]
- [ ] **Tema:** Análisis de relaciones padre-hijo de procesos. (Ej. ¿Por qué `winword.exe` está ejecutando `powershell.exe`?).
- [[Técnica de Caza - Análisis de Relaciones Padre-Hijo.md]]
- [ ] **Actividad Práctica:** Explorar datasets públicos como `Mordor` o `Security Datasets Project` de Splunk, que contienen logs de ataques simulados.
- [[Actividad - Explorar Datasets Públicos de Ataques.md]]
- [ ] **Herramienta a Explorar:** `Splunk Free` o `ELK Stack`. Aprender los fundamentos de su lenguaje de búsqueda (SPL o KQL) para consultar los datos.
- [[Herramientas a Explorar - Splunk y ELK Stack.md]]

### Proyecto Final Sugerido
- [ ] **Objetivo:** Realizar una campaña de caza completa sobre un dataset.
- [[Proyecto Final - Sugerido.md]]
- [ ] **Entregable:** Un informe de Threat Hunt que incluya:
    1. **Hipótesis #1:** Descripción de la hipótesis.
    2. **Consulta:** La consulta exacta usada (ej. en Splunk/KQL).
    3. **Hallazgos:** Lo que encontraste (o no encontraste).
    4. **Conclusión:** Si la actividad era maliciosa, benigna o sospechosa.
    5. Repetir el proceso para 2 hipótesis más.
     [[El Entregable - Informe de Threat Hunt.md]]
