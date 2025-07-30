# Gráficos de Tendencia para Mostrar Evolución

> [!QUOTE] "Para responder a la pregunta '¿estamos mejorando o empeorando?', no hay nada más poderoso que un gráfico de líneas."

**¿Qué es?**
Un gráfico de tendencia, comúnmente un **gráfico de líneas**, se utiliza para visualizar cómo cambia una métrica a lo largo de un período de tiempo continuo (días, meses, trimestres).

### El Caso de Uso: Reporte de Progreso

Quieres demostrarle a la dirección el valor del nuevo programa de gestión de vulnerabilidades que implementaste hace 6 meses.

**Los Datos:** El número total de vulnerabilidades críticas abiertas al final de cada mes:
-   Enero: 50
-   Febrero: 45
-   Marzo: 38
-   Abril: 25
-   Mayo: 18
-   Junio: 12

**El Problema:** La lista de números muestra una mejora, pero no cuenta la historia de forma visual.

**La Solución:** Un gráfico de líneas.

![Gráfico de Tendencia de Vulnerabilidades](https://www.klipfolio.com/sites/default/files/klip-gallery-images/dashboard-security-kpi-vulnerabilities-over-time.png)

### Ventajas del Gráfico de Tendencia

-   **Cuenta una Historia:** Un gráfico de líneas es inherentemente narrativo. La línea descendente en el ejemplo cuenta una historia de éxito y progreso. Una línea ascendente contaría una historia de riesgo creciente que necesita atención urgente.
-   **Identifica Tendencias y Estacionalidad:** Permite ver si los problemas aumentan en ciertos momentos (ej. después de grandes despliegues de software) o si las mejoras son consistentes.
-   **Demuestra el ROI:** Es la mejor herramienta para justificar una inversión. "Desde que invertimos en la Herramienta X en marzo, la tendencia de vulnerabilidades críticas ha disminuido en un 70%."
-   **Permite Proyectar:** Basado en la tendencia histórica, puedes empezar a hacer proyecciones futuras.

### Mejores Prácticas

-   **Elige el Intervalo de Tiempo Correcto:** No muestres datos diarios si la tendencia es mensual.
-   **Etiqueta los Puntos Clave:** Usa anotaciones para marcar eventos importantes en el gráfico (ej. "Implementación del WAF", "Contratación de un nuevo analista"). Esto ayuda a explicar *por qué* la tendencia cambió.
-   **No Sobrecargues:** Evita poner demasiadas líneas en un solo gráfico, ya que se vuelve ilegible. Es mejor tener dos gráficos simples que uno complejo.
