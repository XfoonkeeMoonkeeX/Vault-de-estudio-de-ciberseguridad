# Estándar ISA/IEC 62443

> [!QUOTE] "Si el Modelo Purdue es el mapa, IEC 62443 son las reglas de construcción y las normas de tráfico para la ciudad industrial."

**¿Qué es?**
El `ISA/IEC 62443` es una serie de estándares internacionales que proporcionan un marco de trabajo flexible y completo para la ciberseguridad de los Sistemas de Automatización y Control Industrial (IACS). A diferencia de otros estándares, no solo se enfoca en la tecnología, sino también en las **personas** y los **procesos**.

### Conceptos Clave del Estándar

-   **Roles y Responsabilidades:** El estándar define claramente las responsabilidades de las tres principales partes involucradas:
    1.  **Propietario del Activo (Asset Owner):** La organización que opera el sistema industrial (ej. la compañía eléctrica).
    2.  **Integrador de Sistemas (System Integrator):** La compañía que diseña e instala el sistema de control.
    3.  **Fabricante del Producto (Product Supplier):** La empresa que fabrica los componentes (ej. Siemens, Rockwell).

-   **Zonas y Conductos (Zones and Conduits):** Este es un concepto fundamental que se alinea con el Modelo Purdue.
    -   **Zona:** Un agrupamiento lógico de activos (dispositivos) que comparten requisitos de seguridad comunes. Por ejemplo, todos los PLCs de una línea de producción podrían formar una zona.
    -   **Conducto (Conduit):** El canal de comunicación que conecta dos o más zonas. Aquí es donde se definen y aplican los controles de seguridad de red.

-   **Niveles de Seguridad (Security Levels - SL):** El estándar reconoce que no todos los sistemas necesitan el mismo nivel de protección. Define cuatro niveles de seguridad:
    -   **SL 1:** Protección contra un mal uso casual o accidental.
    -   **SL 2:** Protección contra atacantes con bajos recursos y motivación (ej. "script kiddies").
    -   **SL 3:** Protección contra atacantes sofisticados con recursos y conocimientos específicos de OT (ej. grupos de hacking).
    -   **SL 4:** Protección contra estados-nación con recursos casi ilimitados (ej. los creadores de Stuxnet).

-   **Siete Requisitos Fundamentales (FRs):** El estándar se basa en siete pilares de seguridad que deben ser abordados:
    1.  **Control de Acceso (AC)**
    2.  **Control de Uso (UC)**
    3.  **Integridad del Sistema (SI)**
    4.  **Confidencialidad de los Datos (DC)**
    5.  **Flujo de Datos Restringido (RDF)**
    6.  **Respuesta Oportuna a Eventos (TER)**
    7.  **Disponibilidad de Recursos (RA)**