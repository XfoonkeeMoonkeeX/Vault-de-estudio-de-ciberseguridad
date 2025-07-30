# A01: Broken Access Control (Control de Acceso Roto)

> [!QUOTE] "Solo porque no veas el enlace a la página de administración, no significa que no puedas acceder a ella si la adivinas."

**¿Qué es?** Es la vulnerabilidad más crítica y común en la actualidad. Ocurre cuando un atacante puede acceder a datos o ejecutar acciones que no debería tener permitidas. Falla en hacer cumplir las políticas de quién puede hacer qué.

### Ejemplos Comunes:

-   **Insecure Direct Object References (IDOR):** Es el caso clásico. Un usuario accede a su perfil con una URL como `https://miweb.com/perfil?id=123`. Un atacante simplemente cambia el `id` a `124` y, si el servidor no valida que el usuario logueado es el dueño de la cuenta 124, le mostrará el perfil de otra persona.
-   **Path Traversal:** Un atacante manipula una URL que lee archivos (`https://miweb.com/ver_informe?nombre=reporte_enero.pdf`) para acceder a archivos del sistema, usando `../../../../etc/passwd`.
-   **Elevación de Privilegios:** Un usuario normal descubre la URL del panel de administración (`/admin` o `/dashboard`). Si el sistema no verifica su rol en el servidor, podría acceder a funciones de administrador.

### ¿Cómo Prevenirlo?

-   El principio es: **Denegar por defecto**.
-   Los controles de acceso deben ser centralizados y reutilizables.
-   **Verificar los permisos en el servidor en CADA petición**. No confiar nunca en lo que el cliente (navegador) oculta o muestra.
-   Usar tokens de sesión para identificar al usuario en lugar de `id`s que vienen del cliente.
