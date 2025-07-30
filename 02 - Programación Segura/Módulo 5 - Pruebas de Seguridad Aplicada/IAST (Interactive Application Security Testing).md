# IAST (Interactive Application Security Testing)
*Pruebas Interactivas de Seguridad de Aplicaciones*

> [!QUOTE] "IAST es como darle los planos del edificio al equipo de 'pentesters' y poner sensores de movimiento en cada habitación para ver exactamente qué ruta toman."

-   **¿Qué es?** Es el híbrido de SAST y DAST, a menudo llamado de "caja gris" (**grey-box**).

-   **¿Cómo funciona?** IAST funciona colocando un "agente" dentro de la aplicación en ejecución en un entorno de pruebas. Mientras un tester (manual o una herramienta DAST) interactúa con la aplicación, el agente IAST observa el flujo de datos y el código que se ejecuta por dentro, en tiempo real.

-   **Fortalezas:**
    -   **Lo mejor de ambos mundos:** Combina la visión interna de SAST con la perspectiva externa de DAST.
    -   **Preciso:** Puede confirmar si una vulnerabilidad es explotable y, al mismo tiempo, **indicar la línea exacta de código** que se debe corregir.
    -   **Muy Pocos Falsos Positivos:** Tiene el contexto completo para validar los hallazgos.
    -   **Ideal para APIs:** Es muy eficaz para probar la lógica de las APIs.

-   **Debilidades:**
    -   **Intrusivo:** Requiere "instrumentar" la aplicación con un agente, lo que puede afectar al rendimiento.
    -   **Complejidad:** Puede ser más complejo de configurar que SAST o DAST.
    -   **Dependiente del Lenguaje:** El agente debe ser compatible con el lenguaje de la aplicación.

-   **Herramientas Populares:** `Checkmarx IAST`, `Veracode IAST`, `Contrast Security`, `Synopsys Seeker`.
