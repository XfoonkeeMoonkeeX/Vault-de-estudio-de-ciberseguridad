# Técnica de Caza: "Stacking" o Apilamiento

> [!QUOTE] "En un mundo de normalidad, lo raro es sospechoso. El 'stacking' es la técnica para encontrar lo raro."

**¿Qué es?**
El "stacking" (o apilamiento de datos) es una técnica de análisis de datos que consiste en agrupar y contar la frecuencia de ocurrencia de un valor específico. El objetivo es establecer una línea base (baseline) de lo que es "común" y "normal" en un entorno, para así poder identificar fácilmente lo que es "raro" y "anómalo".

**La Premisa:**
Los administradores de sistemas y el software legítimo tienden a ser consistentes y repetitivos. Los atacantes, a menudo, introducen elementos únicos o poco comunes. **Lo que ocurre millones de veces es probablemente benigno. Lo que ocurre una sola vez, es digno de investigación.**

### ¿Cómo Funciona en la Práctica?

Imagina que tienes los logs de creación de procesos de 10,000 máquinas durante 24 horas.

-   **Stacking de Nombres de Proceso:**
    1.  Agrupas todos los nombres de los procesos ejecutados (`svchost.exe`, `chrome.exe`, `winword.exe`, etc.).
    2.  Cuentas cuántas veces apareció cada uno.
    3.  Ordenas la lista de menor a mayor frecuencia.
    -   **Resultado:** En la parte alta de la lista verás procesos como `svchost.exe` (millones de veces). En la parte baja de la lista (el "long tail"), podrías encontrar algo como `totally_legit.exe` que se ejecutó solo una vez en una máquina. ¡Eso es un excelente punto de partida para una investigación!

-   **Stacking de Hashes de Proceso:**
    -   Incluso mejor que el nombre del proceso. `svchost.exe` es un nombre legítimo, pero un atacante podría nombrar su malware `svchost.exe`. Sin embargo, el **hash** del archivo será diferente.
    -   Si "stackeas" los hashes de todos los `svchost.exe` de tu red, deberías ver unos pocos hashes legítimos (correspondientes a las diferentes versiones de Windows) ejecutándose miles de veces cada uno. Si encuentras un hash de `svchost.exe` que aparece solo una vez, has encontrado un impostor.

-   **Otras aplicaciones del Stacking:**
    -   **Argumentos de la línea de comandos:** ¿Cuál es el comando menos común ejecutado por `powershell.exe`?
    -   **Conexiones de red:** ¿Cuál es el puerto de destino menos común al que se conectan tus máquinas?
    -   **User-Agents de navegador:** ¿Hay algún User-Agent extraño o poco común visitando tu web interna?

Esta técnica es increíblemente poderosa cuando se aplica a grandes volúmenes de datos usando herramientas como Splunk o ELK.
