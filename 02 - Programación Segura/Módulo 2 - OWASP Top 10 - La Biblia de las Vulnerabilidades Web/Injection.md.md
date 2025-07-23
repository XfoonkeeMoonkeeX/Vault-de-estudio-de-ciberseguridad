# A03: Injection (Inyección)

> [!QUOTE] "Tu consulta a la base de datos no es una conversación; es un comando. No dejes que los usuarios cambien tu comando."

**¿Qué es?** Ocurre cuando un atacante puede enviar datos maliciosos a un intérprete (como una base de datos SQL, un servidor LDAP, un sistema operativo) como parte de un comando o consulta. Esto engaña al intérprete para que ejecute comandos no intencionados.

### Tipos Principales y Ejemplos:

-   **SQL Injection (SQLi):** El rey de las inyecciones. Un atacante introduce código SQL en un campo de entrada.
    -   *Ejemplo clásico (Bypass de Login):* En un campo de usuario, el atacante escribe `' OR '1'='1`. Si el código del servidor es: `query = "SELECT * FROM users WHERE user='" + userInput + "'"` la consulta final se convierte en `SELECT * FROM users WHERE user='' OR '1'='1'`, lo que siempre es verdadero y devuelve todos los usuarios, logueando al atacante.
-   **NoSQL Injection:** Similar a SQLi pero para bases de datos NoSQL como MongoDB.
-   **Command Injection:** Una de las más peligrosas. El atacante inyecta comandos del sistema operativo.
    -   *Ejemplo:* Una web permite hacer `ping` a una dirección. Si un atacante introduce `8.8.8.8; rm -rf /`, podría ejecutar el comando de borrado en el servidor.

### ¿Cómo Prevenirlo?

-   La defensa principal contra SQLi es usar **Consultas Parametrizadas (Prepared Statements)**. Esto separa el comando SQL (el código) de los datos.
-   Validar y "sanear" todas las entradas del usuario. Usar listas blancas (permitir solo caracteres conocidos) es mucho más seguro que usar listas negras.
-   Usar un ORM (Object-Relational Mapping) moderno a menudo ayuda, ya que suelen usar consultas parametrizadas por defecto.