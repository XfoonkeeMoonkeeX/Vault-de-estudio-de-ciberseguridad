# ⚔️ Plan de Ataque: Misión Ciberseguridad

> **"La disciplina que aplicaste para planificar tu futuro es la misma energía que te impulsará a través de este plan. La sonrisa con la que te irás a dormir hoy es el combustible para mañana."**

---

### Filosofía del Plan

Este plan está diseñado bajo tres principios fundamentales:

1.  **Consistencia sobre Intensidad:** Es mejor estudiar 2 horas enfocadas cada día que 8 horas un solo día a la semana. Construimos el hábito ladrillo a ladrillo.
2.  **Práctica sobre Teoría:** No aprendemos para saber, aprendemos para **hacer**. Cada sesión de estudio está orientada a una actividad práctica.
3.  **Enfoque Monotarea:** Un ramo, un módulo, una nota a la vez. El multitasking es el enemigo de la profundidad.

---

### El Orden de Batalla (Secuencia de Ramos)

Seguiremos la ruta de construcción lógica que establecimos. Cada ramo se completa antes de empezar el siguiente.

1.  **Fase 1: El Constructor** - `Programación Segura`
2.  **Fase 2: El Detective** - `Threat Hunting (Caza de Amenazas)`
3.  **Fase 3: El Arqueólogo** - `Análisis Forense (DFIR)`
4.  **Fase 4: El Especialista** - `Seguridad IoT / OT`
5.  **Fase 5: El Líder** - `Comunicación de Riesgos`

---

## Tu Ritual Diario (Lunes a Viernes)

Esta es tu rutina. Adáptala a tus horarios, pero intenta mantener la estructura.

**[ ] 0. Preparación (5 minutos)**
-   Siéntate en tu espacio de estudio. Cierra todas las distracciones.
-   Abre Obsidian y lee en voz alta el objetivo del módulo en el que estás.
-   Revisa rápidamente las notas que creaste el día anterior. Refresca la memoria.

**[ ] 1. La Misión del Día (5 minutos)**
-   Abre la nota principal del módulo actual.
-   Identifica el **Tema**, la **Actividad Práctica** o la **Herramienta** que vas a abordar hoy.
-   Abre primero la nota de la **Actividad** o **Herramienta**. Lee el objetivo. Tu cerebro ahora sabe *para qué* va a estudiar la teoría.

**[ ] 2. Bloque de Estudio Enfocado #1 (50 minutos)**
-   Inicia un temporizador.
-   Sumérgete en la(s) nota(s) teórica(s) (`.md`) relacionadas con tu misión del día.
-   **No solo leas.** Toma notas adicionales dentro de las mismas notas de Obsidian. Si una idea te genera una pregunta, escríbela ahí mismo con un `TODO:`.

**[ ] 3. Descanso Activo (10 minutos)**
-   **Levántate.** Aléjate de la pantalla. Estira, camina, hidrátate. No mires el móvil. Deja que tu cerebro procese.

**[ ] 4. Bloque de Práctica #2 (50 minutos)**
-   Inicia un temporizador.
-   Este es el momento de **hacer**.
-   Realiza la **Actividad Práctica** o explora la **Herramienta a Dominar/Explorar**.
-   No te preocupes si no funciona a la primera. El objetivo es intentarlo, encontrarse con los errores y aprender de ellos.

**[ ] 5. Descanso Activo (10 minutos)**
-   Repite el paso 3.

**[ ] 6. El Cierre del Día: Forjando el Nivel (15 minutos)**
-   Este es el paso más importante para "subir de nivel".
-   **Resume (5 min):** En una nueva nota diaria o al final de tu nota principal, escribe 3 frases que resuman lo más importante que aprendiste hoy.
-   **Conecta (5 min):** Abre una nota de un ramo anterior. Encuentra **UNA** conexión con lo que viste hoy. Escribe esa conexión como un comentario.
-   **Traduce (5 min):** Elige **UN** concepto técnico de hoy. Ve a tu "Diccionario de Traducción" personal y añade la traducción al negocio y una analogía.

---

## Tu Primera Semana: Plan de Vuelo

### **Día 1 (Mañana):**
-   **Ramo:** `Programación Segura`
-   **Misión:** Entender el SDL y el Shift Left.
-   **Notas a Estudiar:** `Módulo 1 - La Mentalidad y los Principios.md`, `El Ciclo de Vida de Desarrollo Seguro (Secure-SDL).md`.
-   **Práctica:** Dibuja en un papel el ciclo SDL y explica cada fase en voz alta.

### **Día 2:**
-   **Ramo:** `Programación Segura`
-   **Misión:** Dominar los Principios de Diseño Seguro.
-   **Nota a Estudiar:** `Principios de Diseño Seguro.md`.
-   **Práctica:** Revisa el código de la actividad (`Actividad - Reevaluando Código.md`) e intenta explicar por qué cada cambio mejora la seguridad.

### **Día 3:**
-   **Ramo:** `Programación Segura`
-   **Misión:** Iniciar el asalto al OWASP Top 10.
-   **Notas a Estudiar:** `Módulo 2 - OWASP Top 10.md`, `A01 - Broken Access Control.md`.
-   **Práctica:** En la nota de `Actividad Práctica - OWASP Juice Shop.md`, realiza solo el paso de instalación con Docker. Tenerlo listo te motivará.

### **Día 4:**
-   **Ramo:** `Programación Segura`
-   **Misión:** Continuar con OWASP Top 10.
-   **Notas a Estudiar:** `A02 - Cryptographic Failures.md`, `A03 - Injection.md`.
-   **Práctica:** Abre Juice Shop y Burp Suite. Intenta realizar un ataque de Inyección SQL básico en el login como se describe en la teoría.

### **Día 5:**
-   **Ramo:** `Programación Segura`
-   **Misión:** Dominar la herramienta del atacante web.
-   **Nota a Estudiar/Practicar:** `Herramienta a Dominar - Burp Suite.md`.
-   **Práctica:** Dedica toda la sesión a usar Burp Suite contra Juice Shop. Enfócate en el `Repeater`. Envía peticiones, modifícalas, observa las respuestas.

### **Fin de Semana:**
-   **Opción A (Ligero):** Dedica una hora a repasar las notas de la semana.
-   **Opción B (Intenso):** Dedica un par de horas a jugar libremente con Juice Shop y Burp Suite, intentando resolver los desafíos.
-   **Opción C (Obligatoria):** Descansa. El descanso es parte del plan. Consolida tu conocimiento.

---

> **Última orden del día: Ve a descansar. La misión empieza al amanecer.**
> **Has hecho un trabajo excepcional. Ahora, a ejecutar.**