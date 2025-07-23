
### 🛠️ Actividad Práctica: Mapear un Ataque con MITRE ATT&CK for ICS

> [!check] Objetivo
> Utilizar un framework profesional para organizar y entender las acciones de un atacante en uno de los casos estudiados.

**1. Elige tu Framework:**
-   **MITRE ATT&CK® for ICS** es una base de conocimiento curada de las tácticas y técnicas adversarias observadas en el mundo real contra sistemas de control industrial.
-   **Sitio Web:** [https://attack.mitre.org/matrices/ics/](https://attack.mitre.org/matrices/ics/)

**2. Elige tu Ataque:**
-   Selecciona uno de los ataques: Stuxnet, TRITON o CrashOverride.

**3. El Proceso de Mapeo:**
-   Investiga el ataque en más detalle (hay muchísimos informes técnicos online).
-   Navega por la matriz de ATT&CK for ICS. La matriz está organizada en **Tácticas** (columnas), que representan el "qué" quiere lograr el atacante (ej. Acceso Inicial, Ejecución, Evasión). Cada táctica contiene **Técnicas** (celdas), que son el "cómo" lo logra.
-   Para cada acción que identifiques en el ataque que elegiste, busca la técnica correspondiente en la matriz.
-   **Ejemplo (para Stuxnet):**
    -   **Acción:** Se propagó por USB.
    -   **Táctica:** `Acceso Inicial`
    -   **Técnica:** `T0855: Replication Through Removable Media`
    -   **Acción:** Reprogramó los PLCs.
    -   **Táctica:** `Inhibit Response Function` y `Manipulate Control`
    -   **Técnica:** `T0845: Modify Controller Tasking`

**4. El Entregable (Tus Notas):**
-   En una nueva nota en Obsidian, crea una tabla o una lista.
-   Para el ataque elegido, documenta al menos 5-7 acciones distintas, mapeando cada una a su Táctica y Técnica correspondiente en el framework de MITRE ATT&CK for ICS. Esto te ayudará a pensar como un analista de inteligencia de amenazas.
```