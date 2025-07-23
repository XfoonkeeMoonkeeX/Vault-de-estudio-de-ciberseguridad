# DAST (Dynamic Application Security Testing)
*Pruebas Dinámicas de Seguridad de Aplicaciones*

> [!QUOTE] "DAST es como contratar a un equipo de 'pentesters' para que intente derribar las puertas y ventanas del edificio ya construido, sin darles los planos."

-   **¿Qué es?** Es una metodología de "caja negra" (**black-box**). Analiza la aplicación **mientras está en ejecución**, desde fuera, de la misma manera que lo haría un atacante. No tiene acceso ni conocimiento del código fuente.

-   **¿Cómo funciona?** La herramienta DAST actúa como un hacker automatizado. Envía miles de peticiones maliciosas a la aplicación en ejecución (intentos de inyección, XSS, etc.) y analiza las respuestas para ver si la aplicación es vulnerable.

-   **¿Qué encuentra?**
    -   Cross-Site Scripting (XSS).
    -   Inyección SQL (confirmada, no solo potencial).
    -   Problemas de configuración del servidor (ej. cabeceras HTTP inseguras).
    -   Fallos en la lógica de autenticación y gestión de sesiones.

-   **Fortalezas:**
    -   **Menos Falsos Positivos:** Si una herramienta DAST encuentra algo, generalmente es una vulnerabilidad explotable.
    -   **Independiente del Lenguaje:** Funciona con cualquier tecnología, ya que solo interactúa con la aplicación en ejecución.
    -   **Realista:** Simula ataques del mundo real.

-   **Debilidades:**
    -   **Tardío:** Solo se puede usar cuando la aplicación está completa y desplegada en un entorno de pruebas.
    -   **Lento:** Un escaneo completo puede tardar horas o incluso días.
    -   **Ciego al Código:** No puede identificar la línea de código exacta que causa la vulnerabilidad.

-   **Herramientas Populares:** `OWASP ZAP (Zed Attack Proxy)`, `Burp Suite Pro (Scanner)`, `Invicti`, `Acunetix`.