# Análisis de Composición de Software (SCA)

> [!QUOTE] "Cuando importas una librería, no solo importas su funcionalidad; también heredas sus vulnerabilidades."

El **Análisis de Composición de Software (SCA)** es el proceso automatizado de identificar los componentes de código abierto (librerías, frameworks, dependencias) en la base de código de una aplicación. El objetivo es obtener un inventario completo de lo que estás usando y evaluar los riesgos asociados.

### El Riesgo de las Dependencias de Terceros

1.  **Vulnerabilidades Conocidas (CVEs):** Este es el mayor riesgo. Las librerías populares son mantenidas por humanos y, por lo tanto, tienen bugs. Algunos de esos bugs son vulnerabilidades de seguridad. Cuando se descubre una, se le asigna un identificador único (un **CVE**, de Common Vulnerabilities and Exposures) y se publica. Las herramientas de SCA escanean tus dependencias y las comparan con bases de datos de CVEs para alertarte si estás usando una versión vulnerable.

2.  **Dependencias Transitivas (o Indirectas):** Este es el peligro oculto. Tu proyecto depende de la `Librería A`. Pero para que la `Librería A` funcione, esta a su vez depende de la `Librería B` y la `C`. Si la `Librería C` tiene una vulnerabilidad, ¡tu proyecto también es vulnerable!
    `Tu Proyecto → Librería A → Librería C (Vulnerable)`
    Las buenas herramientas de SCA analizan todo este árbol de dependencias.

3.  **Riesgos de Licencia:** Aunque no es una vulnerabilidad de seguridad, usar una librería con una licencia incompatible con tu proyecto puede tener graves consecuencias legales. Las herramientas de SCA también ayudan a identificar y gestionar las licencias de tus dependencias.

### ¿Cómo Defenderse?

-   **Integrar SCA en tu ciclo de vida de desarrollo (SDL):** Usa herramientas automatizadas que escaneen tus dependencias cada vez que construyes el proyecto.
-   **Mantén tus dependencias actualizadas:** Configura herramientas como **Dependabot** (en GitHub) para que te notifiquen automáticamente cuando una de tus dependencias tiene una actualización de seguridad y te creen un Pull Request para solucionarlo.
-   **Principio de Mínima Superficie de Ataque:** No incluyas librerías que no necesitas. Antes de añadir una nueva dependencia, pregúntate si es realmente necesaria y si confías en sus mantenedores.