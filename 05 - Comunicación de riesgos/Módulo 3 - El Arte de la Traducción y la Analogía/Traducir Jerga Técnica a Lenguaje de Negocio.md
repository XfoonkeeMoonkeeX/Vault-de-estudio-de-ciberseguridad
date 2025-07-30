# Traducir Jerga Técnica a Lenguaje de Negocio

> [!QUOTE] "La dirección no paga por solucionar vulnerabilidades. Paga por reducir riesgos que afectan al negocio."

La traducción efectiva no consiste en "simplificar" los términos, sino en **cambiar el enfoque del problema técnico a la consecuencia para el negocio**. La pregunta clave que debes responder siempre para tu audiencia no técnica es: **"¿Y esto qué significa para nosotros?"**

### El Proceso de Traducción

1.  **Identifica el Hallazgo Técnico:** Sé preciso en lo que encontraste.
    -   *Ejemplo Técnico:* "El servidor de base de datos no tiene los últimos parches de seguridad y es vulnerable a `CVE-2023-XXXX`."

2.  **Determina el Impacto Técnico Inmediato:** ¿Qué permite hacer esta vulnerabilidad a nivel técnico?
    -   *Ejemplo Técnico:* "Esta vulnerabilidad permite a un atacante con acceso a la red interna ejecutar código arbitrario en el servidor de la base de datos."

3.  **Traduce el Impacto Técnico a un Impacto de Negocio:** Este es el paso crucial. Conecta la acción técnica con una consecuencia tangible para la organización.
    -   *Traducción al Lenguaje del Negocio:* "Una falla de seguridad en nuestro sistema de almacenamiento de datos podría permitir a un intruso **acceder, modificar o robar toda nuestra información de clientes**."

4.  **Cuantifica el Riesgo (si es posible):** Añade el contexto financiero o reputacional.
    -   *Traducción al Lenguaje del Negocio (Enriquecida):* "Una falla de seguridad en nuestro sistema de almacenamiento de datos podría permitir a un intruso acceder, modificar o robar toda nuestra información de clientes. Esto no solo nos expondría a **multas regulatorias por incumplimiento de la ley de protección de datos**, sino que también podría **paralizar nuestras operaciones y dañar irreparablemente la confianza de nuestros clientes**."

### Más Ejemplos de Traducción

| Jerga Técnica                                                                      | Traducción al Lenguaje de Negocio                                                                                                         |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| "Un empleado ha sido víctima de un ataque de phishing y sus credenciales han sido comprometidas." | "Un atacante ha obtenido la contraseña de uno de nuestros empleados, dándole acceso a nuestra red interna como si fuera un trabajador legítimo." |
| "Hemos detectado un ataque de Denegación de Servicio (DDoS) contra nuestra página web." | "Nuestra página web está siendo atacada y está fuera de servicio para nuestros clientes, lo que está causando una pérdida directa de ventas."   |
| "El hash de la contraseña de un usuario fue crackeado debido al uso de MD5."         | "El método que usábamos para proteger las contraseñas era anticuado, lo que ha permitido a un atacante descifrar una de ellas."           |

El objetivo es eliminar la jerga (`DDoS`, `MD5`, `hash`) y reemplazarla por el **resultado** (`fuera de servicio`, `descifrar la contraseña`).
