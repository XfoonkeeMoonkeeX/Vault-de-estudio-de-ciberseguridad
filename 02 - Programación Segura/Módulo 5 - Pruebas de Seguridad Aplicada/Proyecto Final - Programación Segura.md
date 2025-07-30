# 🏆 Proyecto Final: Construyendo y Atacando tu Propia Aplicación

---

> [!check] Objetivo Final
> El propósito de este proyecto es pasar del conocimiento teórico a la habilidad práctica demostrable. Construirás una aplicación web desde cero, pero con una diferencia fundamental: aplicarás una mentalidad de seguridad en cada línea de código. Luego, te pondrás el sombrero de un atacante para verificar que tus defensas son sólidas.

### 1. El Desafío: La Aplicación a Construir

Desarrollarás una aplicación web simple pero funcional. Un **blog con registro de usuarios y comentarios** es el escenario perfecto porque toca todos los puntos de interacción críticos.

**Funcionalidades Requeridas:**
- [ ] **Registro de Usuarios:** Los usuarios pueden crear una cuenta (nombre de usuario, email, contraseña).
- [ ] **Inicio de Sesión:** Los usuarios registrados pueden iniciar sesión para autenticarse.
- [ ] **Creación de Posts:** Solo los usuarios autenticados pueden crear nuevas entradas en el blog.
- [ ] **Visualización de Posts:** Cualquier persona (autenticada o no) puede ver los posts.
- [ ] **Añadir Comentarios:** Solo los usuarios autenticados pueden añadir comentarios a los posts.

**Stack Tecnológico Sugerido:**
-   Usa el lenguaje y framework con el que te sientas más cómodo.
-   **Backend:** Python con Flask/Django, Node.js con Express, etc.
-   **Frontend:** HTML simple con plantillas del lado del servidor es suficiente.
-   **Base de Datos:** SQLite es perfecto para este proyecto, ya que es simple y no requiere un servidor separado.

---

### 2. La Metodología: Construyendo con Seguridad en Mente

Mientras construyes, debes aplicar activamente los principios de los módulos anteriores.

-   **Módulo 1 (Mentalidad):** Piensa en la seguridad desde el `git init`. Antes de escribir una función, pregúntate: "¿Cómo podría un atacante abusar de esto?".
-   **Módulo 2 (OWASP):** Tu objetivo es prevenir el Top 10. Concéntrate especialmente en evitar **Inyección** y **Broken Access Control**.
-   **Módulo 3 (Entradas/Salidas):**
    -   **Validación de Entradas:** Aplica validación por **listas blancas** a **TODA** entrada que provenga del usuario (formularios, URLs, etc.).
    -   **Codificación de Salidas:** Asegúrate de que **TODA** salida de datos que se muestra en la página esté **codificada contextualmente** (especialmente los comentarios y nombres de usuario) para prevenir XSS.
-   **Módulo 4 (Dependencias/Secretos):**
    -   Usa una herramienta como `npm audit` o `pip-audit` para verificar tus librerías.
    -   Gestiona tus secretos (como la clave secreta de la sesión o la conexión a la BBDD) usando un archivo `.env` y asegúrate de que esté en tu `.gitignore`.
-   **Módulo 5 (SAST):** Mantén `SonarLint` (o una herramienta similar) activo en tu editor durante todo el proceso para recibir retroalimentación en tiempo real.

---

### 3. El Entregable: ¿Qué Debes Presentar?

**1. El Código Fuente de la Aplicación**
-   El código completo de tu aplicación.
-   Debe incluir un archivo `README.md` con instrucciones claras sobre cómo instalar las dependencias y ejecutar el proyecto.
-   Debe incluir un archivo `.gitignore` que demuestre que no estás subiendo secretos o archivos de entorno.

**2. Informe de "Autohacking"**
-   Este es un documento en formato Markdown donde te conviertes en un pentester. Debes usar **Burp Suite** para atacar tu propia aplicación y documentar los resultados.

> [!example] Estructura del Informe de Autohacking
>
> **a. Introducción:**
> Breve resumen del objetivo: "Este informe detalla los intentos de ataque realizados contra la aplicación de blog para verificar la efectividad de las defensas de seguridad implementadas."
>
> **b. Escenarios de Ataque Probados:**
> Para cada escenario, describe:
> -   **La Vulnerabilidad Probada:** (Ej. Inyección SQL en el formulario de login).
> -   **La Herramienta Usada:** (Ej. Burp Suite Repeater).
> -   **El Payload Utilizado:** (Ej. `admin' OR 1=1; --`).
> -   **El Resultado Obtenido:** (Ej. "La aplicación devolvió un error de 'credenciales inválidas' y no permitió el acceso.").
> -   **Análisis de la Defensa:** **(La parte más importante)** Explica *por qué* el ataque falló. (Ej. "El ataque de SQLi fue prevenido porque la consulta a la base de datos se realizó utilizando consultas parametrizadas, que separan el código de los datos, tratando mi payload como una simple cadena de texto y no como código SQL.").
> -   **Evidencia:** Incluye una captura de pantalla de Burp Repeater mostrando tu petición y la respuesta del servidor.
>
> **c. Lista de Ataques a Probar (Mínimo):**
> -   [ ] **Inyección SQL:** Intenta bypassear el login.
> -   [ ] **Cross-Site Scripting (XSS) Persistente:** Publica un comentario que contenga `<script>alert('XSS')</script>`. ¿Se ejecuta el script cuando se visualiza la página o se muestra el texto inofensivo?
> -   [ ] **Broken Access Control (IDOR):**
>     -   Inicia sesión como `Usuario A`.
>     -   Crea un post. Anota su ID (ej. `/post/5`).
>     -   Intenta editar ese post desde la cuenta del `Usuario B`. ¿Puedes acceder a la página de edición `/post/5/edit`? ¿Puedes enviar la petición de edición directamente con Burp?
>     -   Demuestra que tu código verifica que el usuario logueado es el dueño del recurso antes de permitir una acción.
>
> **d. Conclusión:**
> Un resumen final de la postura de seguridad de la aplicación basado en los resultados de tus pruebas.

Este proyecto no solo te dará una nota; te dará una pieza de portafolio que demuestra que no solo sabes programar, sino que sabes programar de forma **segura**, una de las habilidades más demandadas en la industria.
