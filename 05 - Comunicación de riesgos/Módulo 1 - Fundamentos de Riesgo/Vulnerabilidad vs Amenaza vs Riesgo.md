# Vulnerabilidad vs. Amenaza vs. Riesgo

> [!QUOTE] "Usar estos tres términos de forma intercambiable es el error más común y el que más confunde a la dirección. Un experto debe conocer la diferencia precisa."

Estos tres conceptos son los pilares del análisis de riesgos. Entender su relación es fundamental.

### Vulnerabilidad

-   **Definición:** Una **debilidad** o un "agujero" en un sistema, proceso o control que puede ser explotado.
-   **Naturaleza:** Es una condición pasiva. Es un estado.
-   **Analogía:** Una ventana abierta en el primer piso de una casa.
-   **Ejemplos Técnicos:**
    -   Una versión de Apache sin parches con una vulnerabilidad de RCE conocida.
    -   Una contraseña débil como `Password123`.
    -   La falta de un firewall entre la red de IT y la de OT.
    -   Un empleado sin capacitación en phishing.

### Amenaza (Threat)

-   **Definición:** Cualquier agente o evento con el potencial de causar daño a un activo.
-   **Naturaleza:** Es un agente activo. Es el "quién" o el "qué" podría atacar.
-   **Analogía:** Un ladrón que ronda por el barrio buscando casas a las que entrar.
-   **Ejemplos Técnicos:**
    -   Un grupo de ransomware.
    -   Un empleado descontento (amenaza interna).
    -   Un desastre natural como una inundación.
    -   Un script kiddie escaneando internet en busca de servidores vulnerables.

### Riesgo

-   **Definición:** El **potencial de pérdida o daño** cuando una amenaza explota una vulnerabilidad.
-   **Naturaleza:** Es el resultado, la consecuencia. Es la combinación de la debilidad y el atacante.
-   **Analogía:** El riesgo de que el ladrón (amenaza) vea la ventana abierta (vulnerabilidad) y entre a robar el televisor (impacto).
-   **Ejemplos Técnicos:**
    -   "El **riesgo** de que un grupo de ransomware (amenaza) explote la vulnerabilidad de RCE en nuestro servidor Apache (vulnerabilidad) para cifrar nuestros datos de cliente (impacto)".

### La Relación en una Fórmula

Una forma simple de verlo es:

`Amenaza` + `Vulnerabilidad` = `Riesgo`

**No puede existir un riesgo si falta uno de los componentes.**
-   Si tienes una ventana abierta (vulnerabilidad) pero vives en una isla desierta sin ladrones (sin amenaza), no hay riesgo.
-   Si hay un ladrón muy hábil en tu barrio (amenaza) pero tu casa es un búnker sin ventanas ni puertas (sin vulnerabilidad), no hay riesgo.
