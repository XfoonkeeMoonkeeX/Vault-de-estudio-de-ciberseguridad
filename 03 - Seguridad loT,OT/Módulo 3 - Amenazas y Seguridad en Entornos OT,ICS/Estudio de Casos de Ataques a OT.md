# Estudio de Casos de Ataques a OT

> [!QUOTE] "Para defender una fortaleza, primero debes estudiar cómo otras fortalezas han caído."

El análisis de ataques pasados es la forma más efectiva de entender las Tácticas, Técnicas y Procedimientos (TTPs) de los adversarios en el mundo OT.

### Stuxnet (2010)

-   **Objetivo:** Programa de enriquecimiento nuclear de Irán.
-   **Impacto:** El primer "arma digital" diseñada para causar destrucción física. Stuxnet manipuló la velocidad de las centrifugadoras de uranio, haciéndolas fallar, mientras mostraba a los operadores en sus HMIs que todo funcionaba con normalidad.
-   **TTPs Clave:**
    -   Se propagó a través de USBs para saltar el "air gap" (la separación física) entre la red de IT y la de OT.
    -   Explotó múltiples vulnerabilidades de día cero (0-days) en Windows.
    -   Buscaba un software HMI específico (Siemens WinCC) y luego reprogramaba los PLCs de Siemens.
    -   Ocultó su actividad a los operadores (ataque a la integridad de la visualización).

### TRITON / TRISIS (2017)

-   **Objetivo:** Una planta petroquímica en Arabia Saudita.
-   **Impacto:** El primer malware diseñado específicamente para atacar los **Sistemas Instrumentados de Seguridad (SIS)**, que son los sistemas de "última defensa" que apagan una planta en caso de una emergencia para prevenir desastres. El objetivo del malware era causar una explosión.
-   **TTPs Clave:**
    -   Se enfocó en los controladores SIS de Schneider Electric (modelo Triconex).
    -   El malware se disfrazó de software legítimo y reprogramó los controladores SIS para que no funcionaran en caso de emergencia.
    -   El ataque fue descubierto por un error en el propio malware que provocó que los controladores entraran en modo de fallo seguro y apagaran la planta.

### CrashOverride / Industroyer (2016)

-   **Objetivo:** La red eléctrica de Ucrania.
-   **Impacto:** Causó un apagón masivo en Kiev.
-   **TTPs Clave:**
    -   Fue un malware modular diseñado específicamente para "hablar" los protocolos de las redes eléctricas (IEC 61850, IEC 104).
    -   Podía enviar comandos directamente a los interruptores automáticos de las subestaciones para desconectar la energía.
    -   Incluía un módulo de "wiper" para borrar software en los sistemas y dificultar la recuperación.

---

