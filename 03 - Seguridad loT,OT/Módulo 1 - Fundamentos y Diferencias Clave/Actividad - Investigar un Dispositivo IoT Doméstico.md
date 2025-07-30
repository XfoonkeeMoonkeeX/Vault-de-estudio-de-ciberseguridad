# 🛠️ Actividad Práctica: Investigar un Dispositivo IoT Doméstico

> [!check] Objetivo
> Aplicar los conceptos teóricos del módulo para realizar una investigación de inteligencia de fuentes abiertas (OSINT) sobre un dispositivo IoT común. El objetivo no es "hackearlo", sino entender su arquitectura y superficie de ataque potencial.

### 1. Elige tu Objetivo

Selecciona un dispositivo IoT que tengas en casa o que sea fácil de investigar online.
-   **Buenas opciones:**
    -   Tu Smart TV (Samsung, LG, etc.).
    -   Un asistente de voz (Amazon Echo, Google Home).
    -   Una cámara de seguridad Wi-Fi (Wyze, Ring, etc.).
    -   Un enchufe o bombilla inteligente (TP-Link Kasa, Philips Hue).
    -   Tu router de internet (aunque es más un dispositivo de red, tiene muchas funciones de IoT).

### 2. El Proceso de Investigación (OSINT)

Usa tu navegador y motores de búsqueda para convertirte en un detective digital.

-   **Paso 1: Identificación del Dispositivo**
    -   Encuentra el nombre exacto del modelo y el fabricante del dispositivo. A menudo está en una pegatina en la parte trasera o inferior del mismo.

-   **Paso 2: Documentación y Arquitectura**
    -   Busca el manual de usuario oficial online. A menudo revela información básica sobre la configuración de red.
    -   Busca en la web del fabricante la sección de "desarrolladores" o "API". ¿Ofrecen una API pública? ¿Mencionan los protocolos que usan?
    -   Busca el identificador de la FCC (`FCC ID`), que también suele estar en una pegatina. Búscalo en la web [FCCID.io](https://fccid.io/). A menudo encontrarás fotos internas del dispositivo, los chips que usa y las frecuencias de radio en las que opera.

-   **Paso 3: Investigación de Protocolos**
    -   Busca en Google frases como:
        -   `"protocolo de la cámara Wyze Cam v3"`
        -   `"api del smart tv LG"`
        -   `"cómo se comunica philips hue"`
    -   Intenta identificar si el dispositivo usa **MQTT**, **CoAP**, o protocolos propietarios sobre HTTP/HTTPS. ¿Se comunica directamente con una app en tu teléfono o todo pasa a través de un servidor en la nube (el broker)?

-   **Paso 4: Búsqueda de Vulnerabilidades Conocidas (CVEs)**
    -   Busca en bases de datos de vulnerabilidades el nombre de tu dispositivo.
    -   **Búsquedas útiles en Google:**
        -   `"vulnerabilidades de Amazon Echo"`
        -   `"CVE TP-Link Kasa"`
        -   `"hackear Ring camera"`
    -   Anota si se han encontrado vulnerabilidades en el pasado y de qué tipo eran (ej. fallo en el firmware, credenciales por defecto, falta de cifrado).

### 3. El Entregable (Tus Notas)

En una nueva nota en Obsidian, resume tus hallazgos:
-   **Dispositivo:** Nombre completo del modelo.
-   **Arquitectura de Comunicación:** ¿Cómo "habla" el dispositivo? ¿Con la nube, con el móvil directamente? ¿Cuál parece ser el flujo de datos?
-   **Protocolos Identificados:** Lista los protocolos que crees que utiliza (MQTT, HTTPS, etc.).
-   **Superficie de Ataque Potencial:** Basado en tu investigación, ¿cuáles crees que son los puntos débiles? ¿La conexión Wi-Fi? ¿La app del móvil? ¿El servidor en la nube del fabricante?
-   **Vulnerabilidades Conocidas:** Resume cualquier CVE o incidente de seguridad que hayas encontrado relacionado con tu dispositivo o su fabricante.
