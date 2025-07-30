# 🛠️ Actividad Práctica: Diseñar un Diagrama de Red de una Planta

> [!check] Objetivo
> Aplicar los conceptos de segmentación del Modelo Purdue y los controles de seguridad de red para diseñar una arquitectura de red segura para un escenario industrial simple.

### El Escenario

Imagina que eres el arquitecto de seguridad para una pequeña planta de embotellado de agua. La planta tiene los siguientes activos:

-   **Nivel 0/1 (Zona de Control):**
    -   2 PLCs que controlan las cintas transportadoras y las máquinas de llenado.
-   **Nivel 2 (Zona de Supervisión):**
    -   1 HMI para que los operadores de la planta supervisen y controlen los PLCs.
-   **Nivel 3 (Zona de Operaciones):**
    -   1 Servidor de Historial (Data Historian) que recopila datos de producción de los PLCs.
    -   1 Estación de Ingeniería (Engineering Workstation) usada por los ingenieros para reprogramar los PLCs.
-   **Nivel 4/5 (Red Empresarial / IT):**
    -   1 Servidor de Planificación de Recursos (ERP) que necesita leer los datos de producción del Servidor de Historial.
    -   Acceso a Internet para los empleados.

### Tu Tarea

1.  **Dibuja el Diagrama:**
    -   Usa una herramienta de diagramación. No necesita ser compleja.
    -   **Opciones Gratuitas:** `draw.io` (ahora `diagrams.net`), Lucidchart (tiene plan gratuito), o incluso PowerPoint/Google Slides.
2.  **Aplica el Modelo Purdue:**
    -   Dibuja claramente los diferentes niveles del Modelo Purdue (Nivel 1, 2, 3, DMZ, 4/5).
    -   Coloca cada uno de los activos listados arriba en su nivel correcto.
3.  **Implementa Zonas y Conductos:**
    -   Agrupa los activos en zonas lógicas (ej. "Zona de PLCs", "Zona de Supervisión").
    -   Dibuja los **Firewalls** que separan cada nivel. Coloca un firewall entre el Nivel 3 y la DMZ, y otro entre la DMZ y la Red de IT.
    -   Dibuja una **Zona Desmilitarizada (DMZ) Industrial** entre el entorno de OT (Nivel 3 y abajo) y el de IT (Nivel 4 y arriba).
4.  **Define las Reglas de Comunicación:**
    -   En tu diagrama (o en un texto adjunto), define las reglas de firewall clave. ¿Qué comunicaciones deben permitirse? Sé específico.
    -   **Ejemplo de Reglas:**
        -   Permitir que la HMI (Nivel 2) se comunique con los PLCs (Nivel 1) usando el protocolo Modbus (puerto 502).
        -   Permitir que el Servidor de Historial (Nivel 3) recopile datos de los PLCs (Nivel 1).
        -   **IMPORTANTE:** ¿Cómo obtiene el servidor ERP los datos? No debe conectarse directamente al Servidor de Historial en la red OT. La solución correcta es colocar un **servidor réplica** en la DMZ. El Servidor de Historial envía sus datos (solo en una dirección) a la réplica en la DMZ, y el servidor ERP solo puede hablar con esa réplica.
        -   La Estación de Ingeniería (Nivel 3) necesita acceso para reprogramar los PLCs. Esta es una comunicación muy peligrosa. La regla debe ser muy estricta, quizás solo habilitada durante las ventanas de mantenimiento.

### Entregable

El resultado final será una imagen de tu diagrama de red. Debería mostrar claramente:
-   Los activos en sus niveles correctos.
-   La ubicación de los firewalls.
-   La presencia de una DMZ.
-   Flechas que indican los flujos de comunicación permitidos.
