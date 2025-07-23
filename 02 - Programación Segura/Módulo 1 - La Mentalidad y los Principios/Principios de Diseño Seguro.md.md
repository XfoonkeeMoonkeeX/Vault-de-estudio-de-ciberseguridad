# 🛡️ Módulo 1: Principios de Diseño Seguro

---

> [!INFO] Fundamento Clave
> Los **Principios de Diseño Seguro** son un conjunto de directrices fundamentales y probadas que sirven como base para diseñar, construir y mantener sistemas de software resistentes a ataques. No son reglas rígidas, sino conceptos guía que ayudan a tomar decisiones de arquitectura y desarrollo orientadas a la seguridad desde el inicio.

El objetivo es crear sistemas que sean seguros por defecto, en lugar de intentar parchear la seguridad después de haber sido construidos.

---

## 1. Principio de Mínimo Privilegio (PoLP)

> [!QUOTE] "Nunca le des a un programa más poder del que necesita para hacer su trabajo."

Este es uno de los principios más importantes de la ciberseguridad. [1, 2] Establece que cada componente del sistema (un usuario, un proceso, un programa) debe tener únicamente los permisos mínimos necesarios para realizar su función específica, y nada más.

-   **¿Por qué es crucial?** Si un atacante logra comprometer un componente, el daño se limita a los permisos que ese componente tenía. Se reduce drásticamente el "radio de explosión" de un ataque. [3]

-   **Ejemplo Práctico:**
    -   Un script que solo necesita leer un archivo de configuración no debería tener permisos de escritura o ejecución sobre ese archivo.
    -   Un usuario del departamento de marketing no necesita acceso a la base de datos de desarrollo.
    -   Una aplicación web que se conecta a la base de datos debería usar una cuenta que solo pueda realizar las consultas necesarias (ej. `SELECT`, `INSERT`) en tablas específicas, en lugar de usar el usuario `root` o `admin` de la base de datos. [1]

---

## 2. Defensa en Profundidad

> [!QUOTE] "Un castillo no confía en una sola muralla. Tiene un foso, murallas exteriores, murallas interiores y guardias en cada puerta."

Este principio se basa en la idea de que ninguna medida de seguridad es infalible. [4, 5] Por lo tanto, se deben implementar múltiples capas de controles de seguridad superpuestos y diferentes. Si una capa falla o es vulnerada, la siguiente capa debe estar lista para detener o al menos ralentizar al atacante.

-   **Capas comunes incluyen:**
    -   **Perímetro:** Firewalls de red.
    -   **Red interna:** Segmentación de red, sistemas de detección de intrusiones (IDS).
    -   **Host (Servidor):** Endurecimiento del sistema operativo (hardening), antivirus, firewalls locales.
    -   **Aplicación:** Autenticación robusta, validación de entradas, manejo seguro de sesiones.
    -   **Datos:** Cifrado de datos en reposo y en tránsito. [4, 6]

-   **Ejemplo Práctico:**
    -   Para proteger una base de datos, no solo se limita el acceso por red (firewall), sino que también se exige autenticación (capa de aplicación) y se cifran los datos confidenciales (capa de datos). Si el firewall falla, el atacante aún necesita credenciales. Si las roba, los datos más sensibles siguen estando cifrados.

---

## 3. Reducción de la Superficie de Ataque

> [!QUOTE] "Cuantas menos puertas y ventanas tenga tu casa, más fácil es protegerla."

La superficie de ataque es la suma de todos los puntos (vectores de ataque) a través de los cuales un atacante podría intentar entrar o extraer datos de un sistema. [7, 8] Este principio busca minimizar esas oportunidades.

-   **¿Cómo se reduce?**
    -   Deshabilitando funcionalidades, servicios y puertos que no son necesarios.
    -   Eliminando código innecesario o bibliotecas no utilizadas (código muerto).
    -   Limitando los puntos de entrada de datos a los estrictamente necesarios.
    -   Aplicando el principio de mínimo privilegio para reducir lo que un atacante puede hacer si encuentra una entrada. [7, 9]

-   **Ejemplo Práctico:**
    -   Si una máquina virtual solo va a servir como servidor web, se deben deshabilitar servicios como FTP, SSH (si no es necesario para la administración) y cualquier otro puerto que no sea el 80 (HTTP) y 443 (HTTPS).
    -   Una API no debería exponer `endpoints` (rutas) que son solo para uso interno o de depuración.

---

## 4. Fallar de Forma Segura (Fail-Secure)

> [!QUOTE] "Si algo va a salir mal, que falle en un estado que mantenga la seguridad, no que la abra."

Los sistemas inevitablemente encuentran errores: excepciones de código, fallos de conexión, errores de configuración, etc. Este principio dicta que cuando un sistema falla, debe hacerlo de una manera que deniegue el acceso y mantenga el sistema en un estado seguro, en lugar de conceder permisos o exponer información sensible. [2, 10]

-   **La antítesis es "fallar abierto" (fail-open):** Por ejemplo, una cerradura electrónica que se abre cuando se corta la luz. Eso es aceptable para la seguridad física (salidas de emergencia), pero terrible para la seguridad de los datos.

-   **Ejemplo Práctico:**
    -   Un bloque `try-catch` en el código que gestiona el acceso a un recurso. Si ocurre una excepción inesperada dentro del `try` (ej. no se puede conectar al servidor de autenticación), el bloque `catch` no debe simplemente asumir que el usuario es válido. Debe denegar el acceso por defecto.
    -   Si un firewall de aplicación web (WAF) se reinicia o falla, su estado por defecto debería ser bloquear todo el tráfico hasta que esté operativo de nuevo, no dejar pasar todo sin filtrar. [10]

---
---

## 🔗 Referencias y Fuentes

1.  **[OWASP - Principio de Mínimo Privilegio](https://owasp.org/www-community/Principle_of_Least_Privilege)**: Explicación detallada del principio PoLP.
2.  **[GeeksforGeeks - Principios de Seguridad de la Información](https://www.geeksforgeeks.org/principles-of-information-security/)**: Cubre Mínimo Privilegio y Fallo Seguro.
3.  **[Palo Alto Networks - ¿Qué es el Mínimo Privilegio?](https://www.paloaltonetworks.es/cyberpedia/what-is-the-principle-of-least-privilege)**: Beneficios y aplicación del PoLP.
4.  **[Microsoft - ¿Qué es la Defensa en Profundidad?](https://learn.microsoft.com/es-es/azure/security/fundamentals/defense-in-depth)**: Descripción del concepto aplicado a la nube de Azure.
5.  **[Imperva - Defensa en Profundidad](https://www.imperva.com/learn/application-security/defense-in-depth/)**: Artículo que explica las diferentes capas de seguridad.
6.  **[NIST SP 800-53 (Rev. 5)](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final)**: Estándar de referencia para controles de seguridad, donde la Defensa en Profundidad es un concepto central.
7.  **[OWASP - Reducción de la Superficie de Ataque](https://owasp.org/www-community/Attack_Surface_Analysis_Cheat_Sheet)**: Hoja de trucos para el análisis de la superficie de ataque.
8.  **[Red Hat - ¿Qué es la superficie de ataque?](https://www.redhat.com/es/topics/security/what-is-an-attack-surface)**: Buena definición y estrategias para reducirla.
9.  **[Cloudflare - Reducción de la Superficie de Ataque](https://www.cloudflare.com/es-es/learning/security/threat-management/what-is-attack-surface-reduction/)**: Explica cómo se aplica en el contexto de las aplicaciones web.
10. **[OWASP - Fallar de Forma Segura](https://wiki.owasp.org/index.php/Fail_securely)**: Artículo de la wiki de OWASP sobre el diseño de fallos seguros.