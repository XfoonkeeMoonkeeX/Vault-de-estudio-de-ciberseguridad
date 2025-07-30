# El Modelo Purdue de Arquitectura de Red

> [!QUOTE] "El Modelo Purdue es para la seguridad de OT lo que el Modelo OSI es para las redes de IT: un mapa conceptual para entender cómo se organizan las cosas."

El Modelo Purdue es un estándar de la industria que describe una arquitectura jerárquica para las redes de control industrial. Su principal objetivo es la **segmentación**: separar lógicamente los sistemas de IT de los sistemas de OT para proteger los procesos críticos.

### Los Niveles del Modelo

El modelo se divide en "niveles", desde el proceso físico hasta la red empresarial.

-   **Nivel 5: Red Empresarial (Enterprise Network)**
    -   El mundo de **IT**. Aquí viven los servidores de correo, los sistemas ERP, el acceso a internet, etc.

-   **Nivel 4: Red del Sitio (Site Business Planning)**
    -   Servidores y aplicaciones de IT que gestionan la logística del sitio industrial (planificación de producción, etc.).

---
*Zona Desmilitarizada (DMZ) Industrial*
-   Es una sub-zona entre el Nivel 4 y el 3. Actúa como un "airlock" o zona de amortiguamiento. Los sistemas de IT y OT nunca deben comunicarse directamente; lo hacen a través de servidores proxy o de réplica de datos ubicados en la DMZ.
---

-   **Nivel 3: Operaciones del Sitio (Site-Wide Operations)**
    -   El mundo de **OT** comienza aquí. Sistemas de supervisión y control para toda la planta, como los servidores SCADA y las Estaciones de Historial de Datos (Data Historians).

-   **Nivel 2: Control de Área (Area Control)**
    -   Supervisión y control de áreas específicas del proceso. Aquí se encuentran las **Interfaces Hombre-Máquina (HMI)** que los operadores usan para interactuar con los controladores.

-   **Nivel 1: Control Básico (Basic Control)**
    -   Los "cerebros" del proceso. Aquí residen los **Controladores Lógicos Programables (PLCs)** y los **Controladores de Automatización Programables (PACs)**. Reciben datos de los sensores y envían comandos a los actuadores.

-   **Nivel 0: Proceso Físico (The Process)**
    -   Los dispositivos de campo reales: **sensores** (de temperatura, presión, nivel), **actuadores** (motores, válvulas, bombas) que interactúan directamente con el mundo físico.

> [!check] Principio de Seguridad
> El flujo de comunicación debe ser estrictamente controlado entre niveles. Idealmente, un dispositivo del Nivel 1 nunca debería poder comunicarse directamente con un servidor en el Nivel 4 o 5. Romper esta segmentación es uno de los mayores riesgos en la seguridad de OT.
