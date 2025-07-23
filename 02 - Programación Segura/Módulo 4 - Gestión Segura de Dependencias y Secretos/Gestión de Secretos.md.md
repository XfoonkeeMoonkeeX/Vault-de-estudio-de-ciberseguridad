# Gestión de Secretos

> [!QUOTE] "Commitear una API key a un repositorio público es el equivalente digital a tatuarte la contraseña de tu banco en la frente."

Un "secreto" es cualquier tipo de credencial o información sensible que otorga acceso privilegiado a un sistema.

### ¿Qué se considera un Secreto?
-   Contraseñas de bases de datos
-   Claves de API (de servicios como AWS, Stripe, Google Maps)
-   Tokens de autenticación (JWT secrets)
-   Claves de cifrado y certificados SSL/TLS
-   Cualquier credencial sensible

### El Pecado Capital: ¡Nunca en el Código Fuente!

La peor práctica de seguridad, y una de las más comunes, es "hardcodear" los secretos directamente en el código.

**¿Por qué es un desastre?**
1.  **Historial de Control de Versiones (Git):** Git guarda cada cambio. Aunque borres el secreto en un commit posterior, este permanecerá para siempre en el historial del repositorio, accesible para cualquiera que clone el proyecto.
2.  **Acceso Indebido:** Cualquier persona con acceso de lectura al código fuente (otros desarrolladores, contratistas, o todo el mundo si el repositorio es público) tiene acceso a tus secretos de producción.
3.  **Dificultad de Rotación:** Si una clave de API se ve comprometida, para cambiarla ("rotarla") tienes que modificar el código, hacer pruebas y volver a desplegar toda la aplicación. Un secreto nunca debería requerir un cambio de código.

### La Forma Correcta: Externalizar los Secretos

La estrategia es siempre sacar los secretos del código y cargarlos en la aplicación en tiempo de ejecución.

**Soluciones Populares:**
-   **Variables de Entorno:** Es el método más fundamental y extendido.
    -   Se crea un archivo (comúnmente llamado `.env`) en la raíz del proyecto que contiene los secretos en formato `CLAVE=VALOR`.
    -   La aplicación, al arrancar, lee este archivo y carga los valores como variables de entorno.
    -   **¡CRUCIAL!** El archivo `.env` **NUNCA** se debe subir al repositorio. Se debe añadir una línea con `.env` al archivo `.gitignore`.
-   **Sistemas de Gestión de Secretos (Vaults):** Es la solución a nivel empresarial, mucho más segura y robusta.
    -   **Herramientas:** HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, Google Cloud Secret Manager.
    -   Funcionan como una caja fuerte centralizada. La aplicación se autentica contra el vault al arrancar y solicita los secretos que necesita de forma segura. Permiten auditoría, rotación automática y políticas de acceso granulares.