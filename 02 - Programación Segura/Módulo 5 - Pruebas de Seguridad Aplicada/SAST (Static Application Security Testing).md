# SAST (Static Application Security Testing)
*Pruebas Estáticas de Seguridad de Aplicaciones*

> [!QUOTE] "SAST es como revisar los planos de un edificio en busca de fallos de diseño antes de poner el primer ladrillo."

-   **¿Qué es?** Es una metodología de "caja blanca" (**white-box**). Analiza el **código fuente** de la aplicación, los archivos de configuración y las dependencias **sin ejecutar el programa**.

-   **¿Cómo funciona?** Las herramientas SAST leen tu código y lo comparan con un conjunto de reglas para identificar patrones que son conocidos por ser vulnerables. Piensa en ello como un corrector ortográfico y gramatical, pero para la seguridad del código.

-   **¿Qué encuentra?**
    -   Fallos de Inyección SQL (detecta la concatenación de strings en consultas).
    -   Vulnerabilidades de librerías de terceros (Análisis de Composición de Software - SCA).
    -   Configuraciones inseguras.
    -   Secretos "hardcodeados" en el código.

-   **Fortalezas:**
    -   **Temprano:** Se puede ejecutar muy temprano en el ciclo de vida (incluso mientras el desarrollador escribe código).
    -   **Rápido:** Generalmente es más veloz que otras metodologías de prueba.
    -   **Completo:** Tiene una visión del 100% del código, incluso de las partes que no se usan a menudo.

-   **Debilidades:**
    -   **Falsos Positivos:** Puede generar muchas alertas que no son vulnerabilidades reales en el contexto de la aplicación.
    -   **Ciego al Entorno:** No puede encontrar errores que solo aparecen en tiempo de ejecución, como problemas de configuración del servidor o fallos de lógica de negocio.

-   **Herramientas Populares:** `SonarQube`, `Checkmarx`, `Veracode`, `Snyk Code`, `SonarLint`.
