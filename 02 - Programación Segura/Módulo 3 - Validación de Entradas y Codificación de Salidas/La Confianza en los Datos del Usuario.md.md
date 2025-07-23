# La Confianza en los Datos del Usuario: La Raíz de Casi Todos los Males

> [!QUOTE] "El Axioma Fundamental de la Seguridad Web: **NUNCA CONFÍES EN LOS DATOS PROVENIENTES DEL USUARIO.**"

Este es el principio más importante que un desarrollador debe tatuarse en la mente. Cuando hablamos de "datos del usuario", no nos referimos únicamente a lo que se escribe en un formulario.

**Cualquier dato que provenga de fuera del control directo de tu aplicación es dato del usuario.**

### ¿Qué se considera "Dato del Usuario"?

-   **Campos de formulario:** El más obvio (nombres, contraseñas, comentarios).
-   **Parámetros de la URL (Query String):** Todo lo que va después del `?` en una URL, como `?id=123` o `?busqueda=libros`.
-   **Segmentos de la URL (Ruta):** Partes de la ruta que pueden ser dinámicas, como en `/usuario/123/perfil`.
-   **Cabeceras HTTP (HTTP Headers):** Cabeceras como `User-Agent`, `Referer`, etc. Un atacante puede modificarlas fácilmente.
-   **Cookies:** Aunque las crees tú, el navegador del usuario las almacena y puede manipularlas.
-   **Nombres de archivos subidos:** El nombre del archivo que un usuario sube puede contener código malicioso o intentos de Path Traversal (`../../etc/passwd.jpg`).
-   **Datos de APIs externas:** Si tu aplicación consume datos de otra API, esos datos también deben ser tratados como no confiables.

### La Mentalidad del Atacante

Un desarrollador piensa: "Este campo es para el email del usuario".
Un atacante piensa: "¿Qué pasa si en lugar de un email pongo `' OR 1=1; --`? ¿Y si pongo `<script>alert('XSS')</script>`? ¿Y si envío 10 gigabytes de datos?"

Confiar ciegamente en estos datos es lo que permite las vulnerabilidades más devastadoras:
-   **Inyección SQL:** Si se usan datos de la URL directamente en una consulta a la base de datos.
-   **Cross-Site Scripting (XSS):** Si se muestra el comentario de un usuario en la página sin limpiarlo primero.
-   **Path Traversal:** Si se usa el nombre de un archivo subido para guardarlo en el servidor.

**La solución es una defensa de dos capas: validar todo lo que entra y codificar todo lo que sale.**