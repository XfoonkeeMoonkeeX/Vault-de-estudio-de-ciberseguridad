# Ruta de Aprendizaje: Programación Segura

## Introducción
La seguridad no es algo que se "añade" al final; se "construye" desde el inicio. Este ramo se enfoca en el desarrollo de software resistente a ataques, integrando la mentalidad de un hacker en el ciclo de vida del desarrollo (SDL). El lema aquí es: **"Construir muros, no solo poner alarmas"**.

---

### Módulo 1: La Mentalidad y los Principios
- [ ] **Tema:** El Ciclo de Vida de Desarrollo Seguro (Secure-SDL). El concepto de "Shift Left".
- [[El Ciclo de Vida de Desarrollo Seguro (Secure-SDL).md]]
- [ ] **Tema:** Principios de diseño seguro: Mínimo privilegio, Defensa en profundidad, Reducción de la superficie de ataque, Fallar de forma segura.
- [[Principios de Diseño Seguro.md]]
- [ ] **Actividad:** Tomar un código que hayas escrito en el pasado y re-evaluarlo con estos principios en mente. ¿Qué cambiarías?
- [[Actividad - Reevaluando Código.md]]] ]

### Módulo 2: OWASP Top 10 - La Biblia de las Vulnerabilidades Web
[[OWASP Top 10.md]]
- [ ] **Tema:** Estudiar en profundidad las vulnerabilidades más críticas:
    - A01: Broken Access Control
    - [[Broken Access Control.md]]
    - A02: Cryptographic Failures
    - [[Cryptographic Failures.md]]
    - A03: Injection (SQLi, NoSQLi, Command Injection)
    - [[Injection.md]]
- [ ] **Actividad Práctica:** Desplegar y atacar `OWASP Juice Shop`. Es un laboratorio viviente.
- [[Actividad Práctica - OWASP Juice Shop.md]]
- [ ] **Herramienta a Dominar:** `Burp Suite Community Edition`. Aprender a interceptar, modificar y repetir peticiones web para encontrar fallos.
- [[Herramienta a Dominar - Burp Suite.md]]

### Módulo 3: Validación de Entradas y Codificación de Salidas
[[Validación de Entradas y Codificación de Salidas.md]]
- [ ] **Tema:** La raíz de casi todos los males: la confianza en los datos del usuario.
- [[La Confianza en los Datos del Usuario.md]]
- [ ] **Tema:** Técnicas de validación: listas blancas (permitir solo lo conocido) vs. listas negras (prohibir lo malo).
- [[Técnicas de Validación - Listas Blancas vs Negras.md]]
- [ ] **Tema:** Codificación de salida contextual (Output Encoding). No es lo mismo codificar para HTML, para JavaScript o para una consulta SQL.
- [[Codificación de Salida Contextual.md]]
- [ ] **Actividad:** Escribir funciones de validación robustas para diferentes tipos de datos (email, teléfono, nombres de archivo) en tu lenguaje preferido (Python, JavaScript, etc.).
- [[Actividad - Escribir Funciones de Validación.md]]

### Módulo 4: Gestión Segura de Dependencias y Secretos
[[Gestión Segura de Dependencias y Secretos.md]]
- [ ] **Tema:** Análisis de Composición de Software (SCA). El riesgo de usar librerías de terceros con vulnerabilidades conocidas.
- [[Análisis de Composición de Software (SCA).md]] 
- [ ] **Tema:** Gestión de secretos (API keys, contraseñas de BBDD). ¡Nunca en el código fuente!
- [[Gestión de Secretos.md]]
- [ ] **Actividad:** Escanear las dependencias de un proyecto (ej. con `npm audit` o `pip-audit`).
- [[Actividad - Escanear Dependencias.md]]
- [ ] **Herramienta a Explorar:** `git-secrets` o `truffleHog` para escanear repositorios en busca de secretos accidentalmente "commiteados".
- [[Herramientas a Explorar - git-secrets y truffleHog.md]] 

### Módulo 5: Pruebas de Seguridad Aplicada
- [ ] **Tema:** ¿Qué son las pruebas SAST, DAST e IAST?
    - **SAST (Static Application Security Testing):** Analiza el código fuente sin ejecutarlo.
    - [[SAST (Static Application Security Testing).md]] 
    - **DAST (Dynamic Application Security Testing):** Analiza la aplicación mientras se ejecuta. [[DAST (Dynamic Application Security Testing).md]]
    - IAST (Interactive Application Security Testing):
    - [[IAST (Interactive Application Security Testing).md]]
- [ ] **Actividad:** Instalar una extensión de SAST en tu editor de código (ej. `SonarLint` para VSCode) y ver cómo te alerta de problemas mientras escribes.
   - [[Actividad - Instalar SonarLint en VSCode.md]] 

### Proyecto Final Sugerido
- [ ] **Objetivo:** Desarrollar una aplicación web simple (ej. un blog con registro de usuarios y comentarios).
- [ ] **Entregable:**
    1. El código fuente de la aplicación, implementando las mejores prácticas aprendidas.
    2. Un informe de "autohacking" donde documentes cómo intentaste atacar tu propia aplicación (usando Burp Suite) y cómo las medidas de seguridad que implementaste previnieron esos ataques.
        [[Proyecto Final - Programación Segura.md]] 
