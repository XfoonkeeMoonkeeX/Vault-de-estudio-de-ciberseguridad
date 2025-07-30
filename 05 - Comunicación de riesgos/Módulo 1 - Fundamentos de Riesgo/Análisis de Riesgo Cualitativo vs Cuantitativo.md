# Análisis de Riesgo Cualitativo vs. Cuantitativo

> [!QUOTE] "El análisis cualitativo te dice 'esto duele'. El análisis cuantitativo te dice 'esto duele exactamente por 1.2 millones de dólares'."

Una vez que identificas un riesgo, necesitas medirlo para poder priorizarlo. Hay dos enfoques principales para esto.

### Análisis de Riesgo Cualitativo

-   **¿Qué es?** Es el método más común, rápido y subjetivo. Utiliza escalas descriptivas para clasificar la probabilidad y el impacto.
-   **Escalas:**
    -   **Probabilidad:** Muy Baja, Baja, Media, Alta, Muy Alta.
    -   **Impacto:** Insignificante, Menor, Moderado, Mayor, Crítico.
-   **Proceso:** Se utiliza una **matriz de riesgo (o mapa de calor)**. Se asigna un valor a cada riesgo en la matriz según su probabilidad e impacto. Los riesgos que caen en la esquina superior derecha (Alta Probabilidad / Alto Impacto) son los que deben tratarse primero.
-   **Fortalezas:**
    -   Rápido y fácil de implementar.
    -   No requiere cálculos complejos.
    -   Excelente para una priorización rápida.
-   **Debilidades:**
    -   Es **subjetivo**. Lo que para un analista es "Alto", para otro puede ser "Medio".
    -   No se traduce bien al lenguaje del negocio (dinero). Es difícil justificar una inversión de 50.000€ para mitigar un riesgo "Rojo".

![Matriz de Riesgo Cualitativa](https://www.sixsigmadsi.com/wp-content/uploads/2021/08/Risk-Matrix-Example.png)

---

### Análisis de Riesgo Cuantitativo

-   **¿Qué es?** Es un método más complejo y objetivo que intenta asignar un **valor monetario** al riesgo.
-   **Escalas:** Usa valores numéricos y monetarios.
-   **Proceso:** Requiere el cálculo de varias métricas:
    -   **SLE (Single Loss Expectancy):** ¿Cuánto dinero se perdería *cada vez* que el riesgo se materializa? `SLE = Valor del Activo (AV) x Factor de Exposición (EF)`
    -   **ARO (Annualized Rate of Occurrence):** ¿Cuántas veces *al año* se espera que ocurra este incidente?
    -   **ALE (Annualized Loss Expectancy):** La métrica final. ¿Cuánto dinero se espera perder *al año* por este riesgo? `ALE = SLE x ARO`.
-   **Ejemplo:**
    -   Un servidor de e-commerce (activo) vale 1.000.000€.
    -   Si un ataque de DDoS lo tumba, se espera perder el 20% de los ingresos de un día (Factor de Exposición). `SLE = 1.000.000€ * 0.20 = 200.000€`.
    -   Se espera que un ataque de DDoS de este tipo ocurra 0.5 veces al año (una vez cada dos años). `ARO = 0.5`.
    -   `ALE = 200.000€ * 0.5 = 100.000€ al año`.
-   **Fortalezas:**
    -   Es **objetivo** y basado en datos.
    -   Habla el lenguaje del negocio. Ahora puedes decir: "Propongo invertir 50.000€ en una solución anti-DDoS para mitigar un riesgo que nos cuesta 100.000€ al año. El Retorno de la Inversión en Seguridad (ROSI) es positivo".
-   **Debilidades:**
    -   Es difícil y consume mucho tiempo.
    -   Requiere datos históricos fiables que a menudo no existen. ¿Cómo calculas el valor monetario del "daño a la reputación"?
