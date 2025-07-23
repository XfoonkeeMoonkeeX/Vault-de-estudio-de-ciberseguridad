# 🔬 Módulo 5: Pruebas de Seguridad Aplicada

---

> [!INFO] Fundamento Clave
> La programación segura no se trata solo de escribir código defensivo, sino también de verificar que nuestras defensas funcionan. Este módulo introduce las metodologías automatizadas que nos ayudan a encontrar vulnerabilidades de forma temprana y continua, integrando la seguridad directamente en el flujo de trabajo del desarrollador.

### Ruta de Aprendizaje del Módulo

- [ ] **Tema:** Entender las diferentes filosofías y momentos para probar la seguridad de una aplicación.
    - [[SAST (Static Application Security Testing)]]
    - [[DAST (Dynamic Application Security Testing)]]
    - [[IAST (Interactive Application Security Testing)]]
- [ ] **Actividad Práctica:** Integrar un asistente de seguridad directamente en el editor de código.
    - [[Actividad - Instalar SonarLint en VSCode]]
```*(Nota: He actualizado los enlaces para apuntar a las nuevas notas separadas).*

---

### **2. Nota para SAST**

**Nombre de archivo:** `SAST (Static Application Security Testing).md`
_(Crea una nueva nota con este nombre y pega el siguiente contenido)_

```markdown
# SAST (Static Application Security Testing)
*Pruebas Estáticas de Seguridad de Aplicaciones*

> [!QUOTE] "SAST es como revisar los planos de un edificio en busca de fallos de diseño antes de poner el primer ladrillo."

-   **¿Qué es?** Es una metodología de "caja blanca" (**white-box**). Analiza el **código fuente** de la aplicación, los archivos de configuración y las dependencias **sin ejecutar el programa**.

-   **¿Cómo funciona?** Las herramientas SAST leen tu código y lo comparan con un conjunto de reglas para identificar patrones que son conocidos por ser vulnerables. Piensa en ello como un corrector ortográfico y gramatical, pero para la seguridad del código.

-   **¿Qué encuentra?**
    -   Fallos de Inyección SQL (detecta la concatenación de strings en consultas).
    -   Vulnerabilidades de librerías de terceros (Análisis de Composición de Software - SCA).
    -   Configuraciones inseguras.
    -   Secretos "hardcodeados" en el código.

-   **Fortalezas:**
    -   **Temprano:** Se puede ejecutar muy temprano en el ciclo de vida (incluso mientras el desarrollador escribe código).
    -   **Rápido:** Generalmente es más veloz que otras metodologías de prueba.
    -   **Completo:** Tiene una visión del 100% del código, incluso de las partes que no se usan a menudo.

-   **Debilidades:**
    -   **Falsos Positivos:** Puede generar muchas alertas que no son vulnerabilidades reales en el contexto de la aplicación.
    -   **Ciego al Entorno:** No puede encontrar errores que solo aparecen en tiempo de ejecución, como problemas de configuración del servidor o fallos de lógica de negocio.

-   **Herramientas Populares:** `SonarQube`, `Checkmarx`, `Veracode`, `Snyk Code`, `SonarLint`.