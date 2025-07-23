# Pensar en TTPs, no solo en IoCs

> [!QUOTE] "Un IoC te dice qué buscar. Un TTP te dice cómo buscar."

Este es uno de los cambios de mentalidad más importantes para un cazador de amenazas.

### IoC (Indicator of Compromise)
*Indicador de Compromiso*

-   **¿Qué es?** Es un artefacto estático y forense. Es la "huella dactilar" que un atacante deja atrás.
-   **Ejemplos:**
    -   Un hash de archivo (MD5, SHA256) de un malware conocido.
    -   Una dirección IP o un dominio de un servidor de Comando y Control (C2).
    -   El nombre de un archivo malicioso (`malware.exe`).
-   **Valor:** Son muy útiles para la **detección reactiva**. Si ves este hash o esta IP en tu red, sabes con alta confianza que estás comprometido.
-   **Debilidad:** Son frágiles y fáciles de cambiar. Un atacante puede simplemente recompilar su malware (cambiando el hash) o usar un nuevo dominio/IP. Basar tus defensas solo en IoCs es jugar al "golpea al topo".

---

### TTPs (Tactics, Techniques, and Procedures)
*Tácticas, Técnicas y Procedimientos*

-   **¿Qué son?** Describen el **comportamiento** del adversario. Son el "cómo" y el "porqué" de sus acciones.
-   **Desglose:**
    -   **Táctica:** El objetivo táctico de alto nivel del adversario. *Ejemplo: "Persistencia" (asegurarse de que su malware sobreviva a un reinicio).*
    -   **Técnica:** La forma específica en que el adversario logra esa táctica. *Ejemplo: "Crear una Tarea Programada en Windows."*
    -   **Procedimiento:** La implementación detallada y paso a paso de la técnica por un grupo de atacantes específico. *Ejemplo: "Usar el comando `schtasks.exe /create /sc minute /mo 1 /tn "Updater" /tr "C:\Users\Public\malware.exe"` para ejecutar su malware cada minuto."*

-   **Valor:** Son mucho más duraderos y difíciles de cambiar para un atacante. Un atacante puede cambiar su malware (el IoC), pero probablemente seguirá usando Tareas Programadas para la persistencia (el TTP).
-   **Implicación para el Hunting:** En lugar de buscar un hash específico, el cazador de amenazas busca el **comportamiento de la creación de una tarea programada sospechosa**. Busca eventos de ejecución de `schtasks.exe`, logs de creación de tareas (ID 4698 en Windows), etc.

> [!check] La Pirámide del Dolor (Pyramid of Pain)
> Este concepto, creado por David J. Bianco, ilustra perfectamente esta idea. Muestra que es trivial para un atacante cambiar los hashes y las IPs (la base de la pirámide), pero es muy "doloroso" y costoso para ellos cambiar sus TTPs (la cima de la pirámide). **El objetivo del Threat Hunter es operar en la cima de la pirámide, causando el máximo dolor al adversario.**
> 
> ![Pyramid of Pain](https://detect-respond.io/pyramid.png)