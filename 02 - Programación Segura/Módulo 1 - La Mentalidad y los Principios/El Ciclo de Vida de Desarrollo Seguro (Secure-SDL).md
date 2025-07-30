# 📚 Apuntes: Seguridad en el Desarrollo de Software

---

## 🛡️ Tema 1: El Ciclo de Vida de Desarrollo Seguro (Secure-SDL)

> [!INFO] Definición
> El **Ciclo de Vida de Desarrollo de Software Seguro (SSDLC o Secure-SDL)** es un marco de trabajo que integra la seguridad en cada una de las fases del proceso de desarrollo de software. [2, 5] Su objetivo principal es identificar y mitigar vulnerabilidades y amenazas de seguridad de forma proactiva, desde el inicio hasta el final del ciclo. [1, 3]

A diferencia del modelo de desarrollo tradicional (SDLC), que a menudo dejaba la seguridad para el final, el Secure-SDL la convierte en una responsabilidad compartida y un componente integral en todo el proceso. [[2, 4]]

### Fases del Secure-SDL

Aunque pueden variar según la metodología (cascada, ágil, etc.), las fases generalmente incluyen:

1.  **Requisitos/Planificación:** En esta etapa inicial, se definen los requisitos de seguridad junto con los funcionales. [4, 7, 14] Se realizan evaluaciones de riesgo para comprender las posibles amenazas. [11]
2.  **Diseño:** Se crea un diseño de arquitectura seguro. Una práctica clave aquí es el **Modelado de Amenazas**, que consiste en identificar posibles vectores de ataque y definir contramedidas para mitigarlos. [10, 11]
3.  **Implementación/Desarrollo:** Los desarrolladores escriben el código siguiendo prácticas de codificación segura para evitar vulnerabilidades comunes (como las del **Top 10 de OWASP**). [7, 14] Se utilizan herramientas de análisis estático de código (**SAST**) para detectar fallos de seguridad en tiempo real. [12]
4.  **Verificación/Pruebas:** Se realizan pruebas de seguridad exhaustivas, tanto manuales como automatizadas. Esto incluye análisis dinámico de aplicaciones (**DAST**), pruebas de penetración y revisión de código. [11, 14]
5.  **Despliegue/Lanzamiento:** Antes de pasar a producción, se asegura el entorno de despliegue y se establecen planes de respuesta a incidentes. [1, 14]
6.  **Mantenimiento/Respuesta:** Se monitorea continuamente el software en busca de nuevas vulnerabilidades y se establece un proceso para gestionarlas y aplicar parches de forma eficiente. [1, 7]

---

## ⬅️ Tema 2: El Concepto de "Shift Left"

> [!NOTE] Filosofía Clave
> El término **"Shift Left"** (desplazar a la izquierda) es una filosofía fundamental dentro del Secure-SDL y DevSecOps. [8] Gráficamente, si imaginamos el ciclo de vida del desarrollo en una línea de tiempo de izquierda a derecha, "desplazar a la izquierda" significa mover las prácticas de seguridad a las etapas más tempranas del proceso. [9]

### ¿Por qué es crucial el "Shift Left"?

> [!WARNING] Problemas del Enfoque Tradicional
> Históricamente, la seguridad se aplicaba al final del ciclo ("shift right"), lo que generaba varios problemas:
> *   **Costos elevados:** Corregir una vulnerabilidad en producción es exponencialmente más caro que hacerlo en la fase de diseño o codificación. [2, 15]
> *   **Retrasos en el lanzamiento:** Descubrir fallos graves al final del ciclo puede obligar a retrasar la entrega del producto. [8]
> *   **Mayor riesgo:** Las vulnerabilidades pueden pasar desapercibidas y ser explotadas por atacantes una vez que el software está en producción. [8]

### Principios del "Shift Left":

- **Proactividad:** En lugar de reaccionar a los problemas, se buscan y solucionan de forma proactiva. [8]
- **Automatización:** Se integran herramientas de seguridad automatizadas (SAST, DAST) en los flujos de trabajo de desarrollo (CI/CD) para obtener retroalimentación constante. [12, 14]
- **Responsabilidad del desarrollador:** Se capacita y equipa a los desarrolladores con las herramientas necesarias para que asuman un papel activo en la seguridad, convirtiéndola en una responsabilidad de todos y no solo de un equipo especializado. [4, 5]

> [!TIP] Resumen
> En esencia, el **Secure-SDL** proporciona el **marco estructurado**, mientras que el **"Shift Left"** representa la **mentalidad cultural y operativa** que busca integrar la seguridad de la forma más temprana y eficiente posible. [8, 15]

---
---

## 🔗 Referencias y Fuentes

He verificado todos los enlaces que proporcionaste. La mayoría de ellos funcionan correctamente, pero algunos están rotos o han sido redirigidos. A continuación, te presento la lista corregida y actualizada con enlaces funcionales y relevantes.



# 🛡️ Referencias y Fuentes Corregidas – Secure SDLC

Una recopilación de fuentes confiables y actualizadas sobre el Ciclo de Vida de Desarrollo Seguro (Secure Software Development Lifecycle - Secure SDLC), organizadas para consulta dentro del entorno de estudio en Obsidian.

---

## 🔗 Enlaces Validados

1. **[New Relic – Fases del Secure SDLC](https://newrelic.com/blog/how-to-relic/how-to-leverage-security-in-your-software-development-lifecycle)**  
   Descripción de las fases del Secure SDLC e integración de seguridad desde el inicio.

2. **[Red Hat – Seguridad en el SDLC](https://www.redhat.com/es/topics/security/security-software-development-lifecycle)**  
   Cómo aplicar seguridad en cada etapa del ciclo de vida del desarrollo.

3. **[Checkpoint – Definición de Secure SDLC](https://www.checkpoint.com/es/cyber-hub/cloud-security/what-is-secure-sdlc/)**  
   Definición clara del ciclo de vida seguro del desarrollo de software.

4. **[Wiz.io – ¿Qué es Secure SDLC / SSDLC?](https://www.wiz.io/blog/what-is-secure-sdlc-ssdlc)**  
   Alternativa confiable a enlaces rotos; explicación detallada del concepto.

5. **[Microsoft – The Security Development Lifecycle (SDL)](https://en.wikipedia.org/wiki/Microsoft_Security_Development_Lifecycle)**  
   Visión general del modelo SDL de Microsoft.

6. **[Microsoft Docs – SDL Practices](https://learn.microsoft.com/es-es/azure/security/develop/security-development-lifecycle-overview)**  
   Prácticas y principios oficiales para aplicar SDL.

7. **[Scopic – Seguridad en el Ciclo de Vida del Software](https://scopicsoftware.com/blog/security-in-the-software-development-life-cycle-ssdlc-a-detailed-look/)**  
   Explicación extendida del SSDLC desde una visión de desarrollo ágil.

8. **[Dynatrace – Shift Left vs Shift Right](https://www.dynatrace.com/news/blog/shift-left-vs-shift-right-a-devops-mystery-solved/)**  
   Comparativa entre enfoques de pruebas tempranas y tardías en el desarrollo.

9. **[Red Hat – ¿Qué es Shift Left?](https://www.redhat.com/es/topics/devops/what-is-shift-left)**  
   Introducción clara al enfoque de "Shift Left".

10. **[Microsoft Docs – Threat Modeling Tool](https://learn.microsoft.com/es-es/azure/security/develop/threat-modeling-tool-getting-started)**  
    Herramienta y guía oficial para modelado de amenazas.

11. **[Parasoft – SAST, DAST, IAST y RASP](https://www.parasoft.com/blog/what-are-sast-dast-iast-and-rasp-in-application-security-testing/)**  
    Comparativa técnica entre métodos de pruebas de seguridad.

12. **[OWASP Top 10](https://owasp.org/www-project-top-ten/)**  
    Lista de las vulnerabilidades más críticas según OWASP.

13. **[Parasoft – Pruebas de Seguridad de Aplicaciones](https://www.parasoft.com/solutions/application-security-testing-ast/)**  
    Alternativa moderna para explorar pruebas automatizadas.

14. **[Wiz.io – ¿Qué es Shift Left Security?](https://www.wiz.io/academy/shift-left-security)**  
    Beneficios del enfoque de seguridad desde etapas tempranas.

---

## ✅ Notas

- Todos los enlaces han sido verificados (julio 2025).
- Úsalos como base para reforzar tus notas teóricas y construir vínculos internos en Obsidian.
- Puedes etiquetar esta nota con `#referencias`, `#secure-sdlc`, `#shift-left`.

---

> Actualiza esta lista cada 3-6 meses para evitar enlaces rotos y mantener la calidad del repositorio.
