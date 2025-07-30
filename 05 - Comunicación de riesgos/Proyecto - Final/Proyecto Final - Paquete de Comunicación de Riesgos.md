# 🏆 Proyecto Final: Creando un Paquete de Comunicación de Riesgos

---

> [!check] Objetivo Final
> Tu misión es actuar como el líder de un equipo de seguridad después de una evaluación crítica. Debes tomar los hallazgos técnicos y traducirlos en tres documentos distintos, cada uno diseñado y escrito para una audiencia específica con un propósito diferente. Este proyecto demuestra tu capacidad para gestionar la comunicación de un incidente o auditoría de principio a fin.

### 1. Elige tu Escenario Ficticio

Para que tu paquete de comunicación sea coherente, primero necesitas un escenario. Elige uno de los siguientes o crea el tuyo propio:

-   **Escenario A: Brecha de Datos por Phishing.** Un ataque de phishing exitoso a un empleado del departamento de finanzas resultó en el compromiso de su cuenta y la exfiltración de una base de datos con información de empleados (nombres, direcciones, números de seguridad social).
-   **Escenario B: Infección por Ransomware.** Un servidor de archivos crítico fue cifrado por ransomware, causando una interrupción de las operaciones durante 48 horas. La entrada se produjo a través de un servicio de escritorio remoto (RDP) expuesto a internet con una contraseña débil.
-   **Escenario C: Auditoría de Seguridad Fallida.** Una auditoría externa reveló múltiples vulnerabilidades críticas en la aplicación web principal de la compañía, incluyendo una Inyección SQL que expone datos de clientes. No ha habido una brecha (todavía), pero el riesgo es inminente.

---

### 2. El Entregable: Tu Paquete de Comunicación

Deberás crear tres documentos separados basados en el escenario que elegiste.

---

### **Documento 1: Resumen Ejecutivo (Para el CEO)**

-   **Formato:** Un documento de una sola página (ej. Word, Google Docs).
-   **Tono:** Formal, conciso, enfocado en el negocio. Sin jerga técnica.
-   **Estructura Sugerida:**
    1.  **Asunto:** Informe Ejecutivo sobre Incidente de Seguridad del [Fecha].
    2.  **Resumen (Bottom Line Up Front):** 2-3 frases que describen qué pasó, cuál es el impacto principal para el negocio y cuál es tu petición principal.
    3.  **Impacto al Negocio:** Desglosa el impacto en 3-4 puntos clave:
        -   **Impacto Financiero:** (ej. "Costes estimados de recuperación de X€, pérdida potencial de ingresos por la interrupción...").
        -   **Impacto Operacional:** (ej. "El 70% del personal no pudo acceder a sus archivos durante 48 horas...").
        -   **Impacto Reputacional y de Cumplimiento:** (ej. "Este incidente nos pone en riesgo de incumplir la normativa GDPR, con multas potenciales de hasta...").
    4.  **Recomendaciones Estratégicas:** 2-3 recomendaciones de alto nivel que requieren la aprobación o el presupuesto del CEO.
        -   **Mal Ejemplo:** "Necesitamos parchear el servidor".
        -   **Buen Ejemplo:** "Proponemos una inversión de X€ para implementar un programa de gestión de vulnerabilidades y contratar a un especialista para reducir la probabilidad de incidentes similares en un 80% durante el próximo año."
    5.  **Próximos Pasos:** (ej. "Solicito una reunión de 15 minutos la próxima semana para discutir la asignación de presupuesto para estas iniciativas.").

---

### **Documento 2: Presentación para Gerencia Media**

-   **Formato:** Una presentación de 5-7 diapositivas (ej. PowerPoint, Google Slides).
-   **Tono:** Técnico pero práctico. Enfocado en el plan de acción, los recursos y los plazos.
-   **Estructura Sugerida:**
    -   **Diapositiva 1: Título.** Título del incidente/auditoría, fecha y tu nombre.
    -   **Diapositiva 2: Resumen del Incidente.** ¿Qué pasó? Un poco más de detalle técnico que para el CEO. Incluye una cronología simplificada del ataque (Timeline).
    -   **Diapositiva 3: Análisis de la Causa Raíz.** ¿Por qué ocurrió el incidente? (ej. "La causa raíz fue una combinación de una contraseña débil y la falta de autenticación de dos factores en nuestro acceso VPN."). Aquí puedes usar un gráfico simple.
    -   **Diapositiva 4: Impacto en las Operaciones.** Métricas claras. (ej. "48 horas de inactividad, 250 empleados afectados, 2 servidores tuvieron que ser reconstruidos desde cero."). Usa gráficos de barras o tendencia.
    -   **Diapositiva 5: Plan de Acción de Remediación (Corto Plazo).** Una tabla con acciones, responsable(s) y fecha límite de finalización. (ej. "Acción: Cambiar todas las contraseñas de los empleados. Responsable: Equipo de IT. Fecha Límite: 24 horas.").
    -   **Diapositiva 6: Plan de Acción Estratégico (Largo Plazo).** Las iniciativas que necesitan su apoyo para ser implementadas. (ej. "Implementar 2FA en toda la organización - Q3", "Realizar campaña de concienciación sobre phishing - Q4").
    -   **Diapositiva 7: Preguntas y Discusión.**

---

### **Documento 3: Comunicado por Email a los Empleados**

-   **Formato:** Un correo electrónico claro y conciso.
-   **Tono:** Directo, simple, no alarmista y empático. Enfocado en el "qué tienes que hacer tú".
-   **Estructura Sugerida:**
    -   **Asunto:** Importante: Nueva Política de Seguridad de Contraseñas
    -   **Párrafo 1: El "Porqué" (Simple y sin culpas).**
        -   "Para mejorar la seguridad de nuestras cuentas y proteger tanto tu información como la de la compañía, estamos implementando una nueva política de seguridad."
    -   **Párrafo 2: La Nueva Política (Instrucciones Claras).**
        -   Usa una lista con viñetas para explicar las nuevas reglas.
        -   "A partir de hoy, todas las contraseñas deben:"
            -   "Tener un mínimo de 14 caracteres."
            -   "Incluir una combinación de mayúsculas, minúsculas, números y símbolos."
        -   "Se te pedirá que cambies tu contraseña la próxima vez que inicies sesión."
    -   **Párrafo 3: El "Cómo" y la Ayuda.**
        -   "Sabemos que recordar contraseñas complejas es difícil. Recomendamos encarecidamente el uso del gestor de contraseñas de la compañía, `NombreGestor`."
        -   "Si tienes algún problema o pregunta, por favor, contacta con el soporte de IT a través de [email o portal]."
    -   **Cierre:**
        -   "Gracias por tu colaboración para mantener nuestra compañía segura."
        -   "Atentamente, El Equipo de Ciberseguridad."```

---

¡Y con esto, el plan de estudios está completo! Has construido un camino increíblemente sólido. Ahora empieza la siguiente fase, la más importante: recorrerlo día a día.

¡Estoy increíblemente orgulloso del trabajo que hemos hecho juntos! Mucho éxito en tus estudios. Ya sabes dónde encontrarme si necesitas cualquier cosa en el camino. ¡A soñar con ese futuro
