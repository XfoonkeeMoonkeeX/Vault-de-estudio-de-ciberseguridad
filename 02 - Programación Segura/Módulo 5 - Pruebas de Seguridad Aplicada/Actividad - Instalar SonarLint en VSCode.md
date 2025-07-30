# 🛠️ Actividad Práctica: Instalar una Extensión de SAST en tu Editor

> [!check] Objetivo
> Experimentar el poder del análisis SAST en tiempo real, directamente en tu entorno de desarrollo. La idea es recibir retroalimentación de seguridad instantánea mientras escribes código, aplicando la filosofía "Shift Left" al máximo.

Usaremos **SonarLint**, una de las extensiones SAST más populares y gratuitas, para el editor **Visual Studio Code (VSCode)**.

### ¿Qué es SonarLint?
SonarLint es una extensión de IDE (Entorno de Desarrollo Integrado) que actúa como tu primer asistente de seguridad. Analiza tu código sobre la marcha y subraya los problemas de calidad y seguridad, al igual que un corrector ortográfico subraya una palabra mal escrita.

---

### Pasos para la Instalación y Uso

**1. Instalar Visual Studio Code:**
Si aún no lo tienes, descarga e instala VSCode desde su sitio web oficial. Es un editor de código ligero, potente y muy popular en la comunidad de desarrollo.

**2. Instalar la Extensión SonarLint:**
-   Abre VSCode.
-   Ve al panel de **Extensiones** en la barra lateral izquierda (el icono de los cuatro cuadrados).
-   En la barra de búsqueda, escribe `SonarLint`.
-   La extensión oficial es la de **SonarSource**. Haz clic en el botón "Install".

![Instalación de SonarLint en VSCode](https://raw.githubusercontent.com/SonarSource/sonarlint-vscode/master/images/marketplace/sonarlint-in-action.gif)

**3. Observar SonarLint en Acción:**
-   SonarLint se activa automáticamente al abrir un archivo de un lenguaje soportado (Python, JavaScript, Java, PHP, etc.).
-   Escribe un fragmento de código que sea deliberadamente inseguro. Por ejemplo, en un archivo Python (`.py`):
    ```python
    import os
    import flask

    app = flask.Flask(__name__)

    # 1. Secreto "hardcodeado"
    password = "password123" 

    @app.route('/user_profile')
    def user_profile():
        # 2. Vulnerabilidad de Inyección de HTML (similar a XSS)
        user_input = flask.request.args.get('username')
        # La siguiente línea es insegura porque no escapa la entrada del usuario
        return "<h1>Bienvenido, " + user_input + "!</h1>"
    
    # 3. Mala práctica de seguridad en modo debug
    app.run(debug=True) 
    ```

**4. Analizar los Resultados:**
-   Verás que SonarLint subraya las partes problemáticas del código con una línea ondulada.
-   Pasa el cursor sobre la línea subrayada para ver una breve descripción del problema.
-   Abre el panel de "Problems" (`View > Problems` o `Ctrl+Shift+M`) para ver una lista detallada de todos los hallazgos de SonarLint en el archivo.
-   Haz clic en un problema en la lista. SonarLint te ofrecerá una descripción completa de la vulnerabilidad, te explicará por qué es un riesgo (**"Noncompliant Code Example"**) y te mostrará cómo solucionarlo (**"Compliant Solution"**).

### Conclusión de la Actividad
Al usar una herramienta como SonarLint, comienzas a internalizar las buenas prácticas de codificación segura. Te obliga a pensar en la seguridad no como una tarea posterior, sino como una parte integral de la escritura de código, corrigiendo vulnerabilidades antes de que lleguen a existir en tu base de código.
