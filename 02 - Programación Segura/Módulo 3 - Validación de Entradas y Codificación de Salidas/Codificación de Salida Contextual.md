# Codificación de Salida Contextual (Output Encoding)

> [!QUOTE] "Si la validación de entradas falla, la codificación de salidas es tu última y más fuerte línea de defensa, especialmente contra XSS."

La codificación de salida es el proceso de tomar datos y escapar (convertir) los caracteres que tienen un significado especial en un contexto determinado, para que sean tratados como simples datos y no como código ejecutable.

La palabra clave aquí es **CONTEXTUAL**. La forma en que codificas los datos depende de **dónde** los vas a poner.

### Contexto 1: Cuerpo HTML

-   **Objetivo:** Evitar que un atacante inyecte nuevas etiquetas HTML, como `<script>` o `<img>`.
-   **Técnica:** Codificación de entidades HTML.
-   **Ejemplo:** El navegador interpreta los siguientes caracteres de forma especial:
    -   `<` se convierte en `<` (less than)
    -   `>` se convierte en `>` (greater than)
    -   `&` se convierte en `&` (ampersand)
    -   `"` se convierte en `"` (quote)
    -   `'` se convierte en `'` (single quote)
-   **Resultado:** Si un atacante introduce `<script>alert(1)</script>`, en la página se mostrará el texto literal `<script>alert(1)</script>` en lugar de ejecutarse un script.

### Contexto 2: Atributo HTML

-   **Objetivo:** Evitar que un atacante se "escape" del valor de un atributo para añadir nuevos eventos, como `onmouseover`.
-   **Técnica:** Similar a la codificación HTML, pero especialmente agresiva con las comillas `"` y `'`.
-   **Ejemplo:** En `<input type="text" value="AQUI_VAN_LOS_DATOS">`, si un atacante introduce `"><script>...`, podría cerrar el tag `input` y empezar uno nuevo. La codificación lo previene.

### Contexto 3: Dentro de JavaScript

-   **Objetivo:** Evitar que un atacante termine una cadena de texto y ejecute su propio código JavaScript.
-   **Técnica:** Codificación de cadenas de JavaScript. Se antepone una barra invertida `\` a cualquier carácter no alfanumérico.
-   **Ejemplo:** En `var username = 'AQUI_VAN_LOS_DATOS';`, si un atacante introduce `'; alert('XSS'); //`, la variable se rompería. Después de codificar, se vería como `var username = '\';\ alert(\'XSS\');\ \/\/'`, lo cual es una cadena de texto inofensiva.

### Contexto 4: En una URL

-   **Objetivo:** Evitar que los datos manipulen la estructura de la URL.
-   **Técnica:** Codificación de URL (Percent Encoding).
-   **Ejemplo:** Un espacio se convierte en `%20`, un `=` en `%3D`, etc.

> [!TIP] Usa las herramientas de tu framework
> La buena noticia es que los frameworks web modernos (React, Angular, Vue, Django, Rails, etc.) a menudo realizan la codificación de salida HTML **automáticamente por defecto**. Aprovéchalo. Tu trabajo es entender por qué lo hacen y asegurarte de no desactivar esta protección o de aplicar la codificación correcta cuando trabajas en contextos diferentes.
