# Uso de Mapas de Calor (Heatmaps) para Representar Matrices de Riesgo

> [!QUOTE] "Un mapa de calor convierte una tabla subjetiva en una guía visual inconfundible para la priorización."

**¿Qué es?**
Un mapa de calor (Heatmap) es una representación gráfica de datos donde los valores individuales contenidos en una matriz se representan con colores. Es la visualización perfecta para el **análisis de riesgo cualitativo**.

### El Caso de Uso: La Matriz de Riesgo

Como vimos en el Módulo 1, una matriz de riesgo cruza la **Probabilidad** de un evento con su **Impacto**.

|          | **Bajo Impacto** | **Medio Impacto** | **Alto Impacto** |
| :------- | :--------------: | :---------------: | :--------------: |
| **Alta Prob.** |       Medio      |       Alto        |     Crítico      |
| **Media Prob.**|       Bajo       |       Medio       |       Alto       |
| **Baja Prob.** |       Bajo       |       Bajo        |       Medio      |

**El Problema:** Esta tabla es funcional, pero no visualmente impactante.

**La Solución:** Aplicar un mapa de calor.

Usamos un espectro de color intuitivo (generalmente de verde a rojo) para llenar las celdas:
-   **Verde:** Riesgo bajo (aceptable).
-   **Amarillo/Naranja:** Riesgo medio (requiere monitoreo o acción).
-   **Rojo:** Riesgo alto/crítico (requiere acción inmediata).

![Ejemplo de Mapa de Calor de Riesgos](https://exceline.net/wp-content/uploads/2020/09/Plantilla-de-Matriz-de-riesgos-y-mapa-de-calor.png)

### Ventajas del Mapa de Calor

-   **Priorización Instantánea:** La audiencia puede ver inmediatamente dónde se concentran los riesgos más peligrosos (las celdas rojas). No hay necesidad de leer cada celda.
-   **Lenguaje Universal:** Los colores verde (adelante), amarillo (precaución) y rojo (detenerse) son entendidos globalmente, trascendiendo el lenguaje y la cultura.
-   **Facilita el "Drill-Down":** Puedes presentar un mapa de calor de alto nivel a los ejecutivos y luego hacer clic o mostrar los riesgos específicos que componen cada celda de color para los gerentes técnicos.

**Cómo Crearlo:**
Herramientas como Excel y Google Sheets tienen funciones de "formato condicional" que te permiten crear mapas de calor a partir de una tabla de datos en segundos.