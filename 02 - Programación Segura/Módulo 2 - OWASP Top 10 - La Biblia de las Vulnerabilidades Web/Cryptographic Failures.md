# A02: Cryptographic Failures (Fallas Criptográficas)

> [!QUOTE] "Guardar una contraseña en texto plano es como dejar las llaves de tu casa debajo del felpudo."

**¿Qué es?** Se refiere a fallos relacionados con la criptografía (o la falta de ella), que a menudo exponen datos sensibles. No solo se trata de *no* cifrar, sino de hacerlo de forma débil o incorrecta.

### Ejemplos Comunes:

-   **Transmisión de datos en texto plano:** Usar HTTP en lugar de **HTTPS (TLS)**. Cualquiera en la red (ej. un Wi-Fi público) puede leer todo el tráfico, incluyendo contraseñas y cookies de sesión.
-   **Uso de algoritmos de hashing débiles o rotos:** Almacenar contraseñas usando `MD5` o `SHA1`. Estos son extremadamente rápidos de romper con tablas precalculadas (rainbow tables). Se deben usar algoritmos modernos y lentos como **Bcrypt**, **Scrypt** o **Argon2**.
-   **Secretos "hardcodeados":** Escribir claves de API, contraseñas de bases de datos o frases secretas directamente en el código fuente.
-   **Cifrado sin autenticación:** Usar un modo de cifrado que no garantiza que los datos no hayan sido manipulados por un atacante (ej. AES en modo ECB).

### ¿Cómo Prevenirlo?

-   Forzar HTTPS en toda la aplicación.
-   Usar hashes fuertes, modernos y con "sal" (salt) para todas las contraseñas.
-   No almacenar datos sensibles si no es estrictamente necesario. Si se debe hacer, cifrarlos en reposo.
-   Cargar los secretos desde variables de entorno o sistemas de gestión de secretos (Vaults), nunca desde el código.
