# Gráficos de Barras para Comparar Severidades

> [!QUOTE] "Cuando necesitas responder a la pregunta '¿cuánto tenemos de cada cosa?', el gráfico de barras es tu mejor aliado."

**¿Qué es?**
Un gráfico de barras utiliza barras rectangulares (verticales u horizontales) para representar y comparar valores entre diferentes categorías.

### El Caso de Uso: Inventario de Vulnerabilidades

Después de realizar un escaneo de vulnerabilidades en 100 servidores, obtienes los siguientes datos:
-   Vulnerabilidades Críticas: 15
-   Vulnerabilidades Altas: 42
-   Vulnerabilidades Medias: 110
-   Vulnerabilidades Bajas: 250

**El Problema:** La lista de números es informativa, pero no transmite la urgencia ni la proporción.

**La Solución:** Un gráfico de barras simple.

![Gráfico de Barras de Vulnerabilidades](https://www.tenable.com/sites/drupal.dmz.tenable.com/files/images/blog/2021/Screen-Shot-2021-04-12-at-10.45.19-AM.png)

### Ventajas del Gráfico de Barras

-   **Comparación Intuitiva:** El ojo humano es excelente para comparar longitudes. Es inmediatamente obvio que la barra de "Medias" es más grande que la de "Altas", y que la barra de "Críticas" es la más pequeña pero potencialmente la más peligrosa.
-   **Claridad en las Categorías:** Funciona perfectamente para datos categóricos discretos (Crítica, Alta, Media, Baja no son un continuo).
-   **Flexibilidad:** Puedes "apilar" las barras para mostrar sub-categorías. Por ejemplo, cada barra de severidad podría estar dividida por colores para mostrar qué porcentaje de esas vulnerabilidades son del tipo "Servidor Web" o "Base de Datos".

### Mejores Prácticas

-   **Ordena las Barras:** Ordena las categorías de forma lógica (ej. de mayor a menor severidad, o de mayor a menor cantidad).
-   **Usa el Color con Propósito:** Usa los mismos colores que en tu mapa de calor (Rojo para Críticas, Naranja para Altas, etc.) para mantener la consistencia visual en tu informe.
-   **Etiquetas Claras:** Asegúrate de que los ejes y las barras estén claramente etiquetados. No hagas que tu audiencia adivine qué significan los números.
-   **Mantén la Simplicidad:** Evita los efectos 3D, las sombras y los fondos complejos. El objetivo es la claridad, no el arte.
