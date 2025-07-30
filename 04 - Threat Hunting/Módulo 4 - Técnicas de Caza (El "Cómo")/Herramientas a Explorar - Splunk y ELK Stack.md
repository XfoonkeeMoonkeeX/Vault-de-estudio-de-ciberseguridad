# 🛠️ Herramientas a Explorar: Splunk y ELK Stack

> [!tool] ¿Qué son?
> Splunk y el ELK Stack son plataformas de **SIEM (Security Information and Event Management)** y análisis de logs a gran escala. Son los "motores de búsqueda" para los datos de seguridad de una organización. Permiten ingestar, indexar, buscar y visualizar terabytes de logs de cientos de fuentes diferentes en un solo lugar. Para un Threat Hunter, son su herramienta de trabajo principal.

### Splunk

-   **Descripción:** Es la plataforma comercial líder en el mercado de SIEM. Es extremadamente potente, rápida y tiene un ecosistema enorme de aplicaciones y dashboards pre-construidos.
-   **Lenguaje de Búsqueda:** **SPL (Search Processing Language)**. Es un lenguaje basado en tuberías (`|`), muy intuitivo.
-   **Versión Gratuita:** **Splunk Enterprise Free** permite ingestar hasta 500 MB de datos al día, lo cual es más que suficiente para un laboratorio en casa.
-   **Ejemplo de Búsqueda (SPL):**
    > "Muéstrame los 10 procesos menos comunes que se han ejecutado, basándome en los logs de Sysmon."
    ```splunk
    index="sysmon" sourcetype="xmlwineventlog" EventCode=1 
    | stats count by ProcessName 
    | sort count asc 
    | head 10
    ```

### ELK Stack (Elastic Stack)

-   **Descripción:** Es la alternativa de código abierto más popular a Splunk. Es igualmente potente pero puede ser más complejo de configurar y mantener.
-   **Componentes:** ELK es un acrónimo de sus tres componentes principales:
    -   **E - Elasticsearch:** El motor de búsqueda y base de datos distribuida.
    -   **L - Logstash:** El motor de ingesta y procesamiento que normaliza los logs antes de enviarlos a Elasticsearch.
    -   **K - Kibana:** La interfaz web para buscar, analizar y visualizar los datos con dashboards.
-   **Lenguaje de Búsqueda:** **KQL (Kibana Query Language)** o Lucene.
-   **Ejemplo de Búsqueda (KQL):**
    > "Muéstrame los eventos de creación de proceso donde el padre fue `winword.exe` y el hijo fue `powershell.exe`."
    ```kql
    winlog.event_id:1 AND winlog.process.parent.name:"winword.exe" AND winlog.process.name:"powershell.exe"
    ```

### Tu Misión de Exploración

1.  **Elige una plataforma.** Para empezar, **Splunk Free** es probablemente más fácil de poner en marcha.
2.  **Instálala** en una máquina virtual (Linux es ideal para esto). Sigue las guías de instalación oficiales.
3.  **Ingesta los datos.** Toma uno de los datasets de `Mordor` que ya están preparados para Splunk y sigue las instrucciones para ingestarlo.
4.  **Realiza tus primeras búsquedas.** Abre la interfaz web de Splunk y empieza a jugar con SPL.
    -   Intenta replicar las búsquedas de las notas anteriores.
    -   Usa el comando `stats count by <field>` para practicar la técnica de **stacking**.
    -   Filtra por EventCodes de Sysmon.

Aprender el lenguaje de búsqueda de una de estas plataformas es una de las habilidades más valiosas y demandadas para cualquier rol de ciberseguridad defensiva.
