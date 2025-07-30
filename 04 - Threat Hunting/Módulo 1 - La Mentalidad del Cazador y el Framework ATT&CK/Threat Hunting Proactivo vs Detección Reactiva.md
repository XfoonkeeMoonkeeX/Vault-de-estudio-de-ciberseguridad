# Threat Hunting Proactivo vs. Detección Reactiva

> [!QUOTE] "La detección reactiva juega a la defensa. El threat hunting juega al ataque, dentro de tu propia red."

Para entender el valor del Threat Hunting, primero hay que entender el modelo de seguridad tradicional del que nace.

### Detección Reactiva (El Modelo del SOC Tradicional)

-   **Mentalidad:** "Asumimos que estamos seguros hasta que una alarma nos diga lo contrario."
-   **Funcionamiento:** Se basa en herramientas de seguridad automatizadas que generan alertas.
    -   Un **Antivirus (AV)** o **Endpoint Detection and Response (EDR)** detecta un hash de archivo malicioso.
    -   Un **Sistema de Detección de Intrusiones (IDS)** detecta una firma de red de un exploit conocido.
    -   Un **SIEM (Security Information and Event Management)** correlaciona logs y genera una alerta basada en una regla predefinida (ej. "100 intentos de login fallidos en 1 minuto").
-   **Flujo de Trabajo:** Una **alerta** se dispara -> un **analista del SOC de Nivel 1** la investiga -> si es un positivo verdadero, lo escala a un **analista de Nivel 2** o al **equipo de Respuesta a Incidentes (IR)**.
-   **Limitación Principal:** Este modelo es efectivo contra amenazas conocidas, masivas y "ruidosas". Falla contra **amenazas avanzadas y sigilosas (APTs)** que utilizan técnicas novedosas, malware personalizado o abusan de herramientas legítimas del sistema para no ser detectados.

---

### Threat Hunting Proactivo

-   **Mentalidad:** "**Asumimos que estamos comprometidos.** El atacante ya está dentro. Mi trabajo es encontrarlo antes de que logre su objetivo."
-   **Funcionamiento:** No espera una alerta. Es un proceso iterativo y dirigido por humanos, donde un analista experto (el Hunter) formula una hipótesis sobre una posible actividad maliciosa y busca activamente la evidencia para confirmarla o refutarla.
-   **Flujo de Trabajo:** Un **Hunter** formula una **hipótesis** (ej. "Supongo que un atacante podría estar usando Tareas Programadas de Windows para persistencia") -> el Hunter **investiga** los logs de creación de tareas, eventos de ejecución, etc., buscando anomalías -> si encuentra algo, inicia un proceso de **Respuesta a Incidentes**.
-   **Ventaja Principal:** Es la única forma efectiva de detectar adversarios avanzados que han eludido todas las defensas automatizadas. Encuentra lo "desconocido desconocido".

> [!check] Analogía
> -   **Detección Reactiva:** Es un detector de metales. Pita cuando encuentra un objeto metálico conocido.
> -   **Threat Hunting:** Es un geólogo con un radar de penetración terrestre. No busca metal, busca anomalías y formaciones extrañas bajo la superficie que podrían *indicar* la presencia de algo valioso... o peligroso.
