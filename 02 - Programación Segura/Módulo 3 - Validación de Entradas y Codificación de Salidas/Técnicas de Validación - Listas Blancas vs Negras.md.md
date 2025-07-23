# Técnicas de Validación: Listas Blancas vs. Listas Negras

> [!QUOTE] "Para proteger una ciudad, es más fácil tener una lista de invitados permitidos que una lista de todos los criminales del mundo."

La validación de entradas es el proceso de aplicar un conjunto de reglas estrictas a los datos que entran a tu aplicación. Si los datos no cumplen las reglas, se rechazan. Existen dos enfoques principales para esto.

---

### Listas Negras (Blacklisting) - El Enfoque Débil

-   **¿Qué es?** Consiste en definir una lista de caracteres o patrones "malos" conocidos y prohibirlos. Se permite todo excepto lo que está explícitamente prohibido.
-   **Ejemplo:** "No permitir la palabra `<script>` para prevenir XSS".

-   **¿Por qué es una mala idea?**
    -   **Es una batalla perdida:** Un atacante siempre encontrará una forma de saltarse la lista. ¿Qué pasa si escriben `<SCRIPT>` (mayúsculas)? ¿O `<scr<script>ipt>` (un script dentro de otro)? ¿O usan una codificación diferente como `%3Cscript%3E`?
    -   **El universo de lo "malo" es infinito:** Es imposible predecir todas las posibles entradas maliciosas que un atacante creativo pueda inventar.

> [!WARNING] Conclusión sobre Listas Negras
> **Nunca uses listas negras como tu única defensa.** Son frágiles, fáciles de eludir y crean una falsa sensación de seguridad.

---

### Listas Blancas (Whitelisting) - El Enfoque Fuerte

-   **¿Qué es?** Consiste en definir un formato estricto de lo que es **aceptable y bueno**. Se prohíbe todo excepto lo que está explícitamente permitido.
-   **Ejemplo:** "Para un campo de código postal de 5 dígitos, solo se permiten exactamente 5 caracteres, y cada uno debe ser un número entre 0 y 9. Cualquier otra cosa se rechaza."

-   **¿Por qué es el mejor enfoque?**
    -   **El universo de lo "bueno" es finito y bien definido:** Tú controlas las reglas. Si defines que un nombre de usuario solo puede contener letras, números y guiones bajos, y debe tener entre 3 y 15 caracteres, has reducido drásticamente la superficie de ataque.
    -   **Seguro por defecto:** No necesitas conocer todos los trucos de los atacantes. Simplemente rechazas cualquier cosa que no se ajuste a tu estricta definición de "normal".

> [!check] Conclusión sobre Listas Blancas
> **Usa siempre listas blancas para la validación de entradas.** Define el tipo de dato, el formato, la longitud y el rango de valores permitidos. Es el método más robusto y seguro.