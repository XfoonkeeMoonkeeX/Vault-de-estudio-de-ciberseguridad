
🛠️ Actividad Práctica: Redactar Resúmenes para Diferentes Audiencias

> [!check] Objetivo
> Tomar un único hallazgo técnico y "traducirlo" a los tres lenguajes diferentes de las audiencias clave. Este ejercicio entrena tu habilidad para cambiar de perspectiva y comunicar el mismo problema con diferentes enfoques y objetivos.

### El Hallazgo Técnico

> **"Se ha descubierto una vulnerabilidad de Cross-Site Scripting (XSS) Almacenado en el campo de comentarios de nuestro blog corporativo. Un atacante puede inyectar código JavaScript malicioso que se almacenará en nuestra base de datos y se ejecutará en el navegador de cualquier usuario que visite la página del post."**

---

### Tu Tarea

Escribe tres resúmenes de un solo párrafo (máximo 3-4 frases cada uno) para comunicar este hallazgo a cada una de las siguientes audiencias.

---

### Resumen #1: Para el CEO (C-Suite)

-   **Objetivo:** Conseguir aprobación para asignar recursos y priorizar la solución.
-   **Enfoque:** Riesgo para el negocio, reputación, confianza del cliente.

**[Escribe aquí tu resumen para el CEO]**

*Pista: Piensa en el impacto. ¿Qué podría hacer ese código JavaScript? Robar las cookies de sesión de los clientes, redirigirlos a sitios de phishing, desfigurar la web con contenido ofensivo. Traduce eso a un riesgo de negocio.*

> **Ejemplo de Respuesta:**
> "Hemos identificado un riesgo de seguridad en nuestro blog corporativo que podría permitir a un atacante manipular el contenido de nuestra web y potencialmente robar información de los visitantes. Esto expone a la compañía a un daño reputacional significativo y a una pérdida de confianza del cliente. Recomiendo asignar recursos de desarrollo de inmediato para remediar este problema y proteger la imagen de nuestra marca."

---

### Resumen #2: Para el Gerente de Desarrollo (Gerente Técnico)

-   **Objetivo:** Que entienda la severidad técnica y planifique la remediación.
-   **Enfoque:** Impacto operativo, causa raíz, solución técnica.

**[Escribe aquí tu resumen para el Gerente de Desarrollo]**

*Pista: Sé más técnico, pero enfócate en la acción. Menciona la vulnerabilidad y la solución recomendada (codificación de salida).*

> **Ejemplo de Respuesta:**
> "El campo de comentarios del blog carece de codificación de salida, lo que ha introducido una vulnerabilidad crítica de XSS Almacenado. Necesitamos priorizar un parche en el próximo sprint para implementar una librería de codificación contextual (como la de OWASP ESAPI) en el backend antes de renderizar los comentarios. Estimo que esto tomará unas 8 horas de trabajo de un desarrollador para asegurar que todos los datos mostrados sean tratados como texto y no como código ejecutable."

---

### Resumen #3: Para los Usuarios Finales (Equipo de Marketing que usa el Blog)

-   **Objetivo:** Que entiendan la situación temporalmente y sepan qué hacer (en este caso, no hay acción directa para ellos, es más una comunicación informativa).
-   **Enfoque:** Simple, sin alarmismo, enfocado en el impacto visible.

**[Escribe aquí tu resumen para los Usuarios Finales]**

*Pista: La simplicidad es la clave. Evita la jerga técnica como "XSS" o "JavaScript". Explícalo en términos de lo que podrían ver.*

> **Ejemplo de Respuesta:**
> "El equipo de seguridad está trabajando para solucionar un problema en la sección de comentarios del blog que podría permitir que se muestre contenido inapropiado o que los enlaces no funcionen correctamente. No se requiere ninguna acción por su parte en este momento. Les notificaremos en cuanto el problema esté completamente resuelto. Gracias por su comprensión."
```
