# Opciones de Tratamiento del Riesgo

> [!QUOTE] "Una vez que conoces un riesgo, ignorarlo no es una opción. Tienes que tomar una decisión estratégica."

Después de identificar y analizar un riesgo, una organización debe decidir qué hacer con él. Hay cuatro opciones estratégicas principales para el tratamiento del riesgo.

### 1. Mitigar (Mitigate / Remediate)

-   **¿Qué es?** Es la respuesta más común en ciberseguridad. Consiste en **aplicar controles de seguridad** para reducir la probabilidad o el impacto del riesgo (o ambos).
-   **Objetivo:** Reducir el riesgo a un nivel aceptable.
-   **Ejemplo:**
    -   **Riesgo:** Un atacante podría explotar una vulnerabilidad en nuestro servidor web.
    -   **Mitigación:** Aplicar el parche de seguridad (reduce la probabilidad), instalar un Web Application Firewall (WAF) (reduce la probabilidad), y tener copias de seguridad robustas (reduce el impacto).

### 2. Aceptar (Accept / Tolerate)

-   **¿Qué es?** Es la decisión consciente e informada de **no hacer nada** y aceptar las consecuencias si el riesgo se materializa.
-   **¿Cuándo se hace?** Se aplica cuando el coste de mitigar el riesgo es mayor que el coste del impacto potencial.
-   **Ejemplo:**
    -   **Riesgo:** Un atacante podría desfigurar una página web de marketing poco importante.
    -   **Análisis:** El impacto es muy bajo (solo daño reputacional menor) y la probabilidad es media. El coste de implementar un WAF y otros controles es de 20.000€. El coste de restaurar la página desde una copia de seguridad es de 500€.
    -   **Decisión:** La organización **acepta** formalmente el riesgo.

> [!WARNING] Aceptación Formal
> La aceptación del riesgo debe ser una decisión formal, documentada y aprobada por la dirección. No es lo mismo que la ignorancia.

### 3. Transferir (Transfer / Share)

-   **¿Qué es?** Consiste en pasar una parte o la totalidad del impacto financiero del riesgo a un tercero.
-   **Ejemplo Clásico:** Comprar un **seguro**.
-   **Ejemplo:**
    -   **Riesgo:** Un ataque de ransomware podría costar 1 millón de euros en recuperación y pérdida de negocio.
    -   **Transferencia:** La organización contrata una **póliza de ciberseguro** que cubre los costes de respuesta a incidentes de ransomware.
-   **Importante:** Transferir el riesgo no elimina la responsabilidad. La organización sigue sufriendo el daño reputacional y operacional, solo se transfiere la carga financiera.

### 4. Evitar (Avoid)

-   **¿Qué es?** Es la decisión de **eliminar por completo la actividad o el sistema** que da origen al riesgo.
-   **¿Cuándo se hace?** Cuando el riesgo es tan alto que ninguna medida de mitigación, aceptación o transferencia es viable.
-   **Ejemplo:**
    -   **Actividad:** Una compañía planea lanzar una nueva aplicación móvil para permitir pagos.
    -   **Análisis de Riesgo:** El análisis determina que el riesgo de fraude y el cumplimiento de la normativa PCI-DSS son demasiado altos y costosos para la organización en este momento.
    -   **Decisión:** La organización decide **evitar** el riesgo cancelando el desarrollo de la funcionalidad de pagos en la aplicación.
