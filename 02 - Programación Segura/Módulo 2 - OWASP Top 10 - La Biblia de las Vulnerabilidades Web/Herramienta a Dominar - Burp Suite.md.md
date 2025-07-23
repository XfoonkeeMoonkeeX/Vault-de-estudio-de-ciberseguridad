# 🛠️ Herramienta a Dominar: Burp Suite Community Edition

> [!tool] ¿Qué es?
> Burp Suite es tu navaja suiza para el hacking web. Es un **proxy de interceptación** que se sienta entre tu navegador y el servidor de la aplicación web. Te permite ver, modificar, repetir y analizar cada petición HTTP/HTTPS que tu navegador envía, dándote un control total sobre la comunicación.

### 1. Lanzamiento en Kali Linux

Burp Suite ya viene preinstalado en Kali Linux. Simplemente búscalo en el menú de aplicaciones, a menudo en la categoría de "Análisis de Aplicaciones Web".

### 2. Configuración del Proxy (Pasos Críticos)

Para que Burp funcione, debes decirle a tu navegador que envíe todo su tráfico a través de él.

-   **Paso 1: Configurar el Navegador con FoxyProxy**
    -   La forma más fácil y estándar es usar la extensión de navegador **FoxyProxy** (disponible para Firefox y Chrome).
    -   Instala FoxyProxy y configúralo para crear un nuevo perfil de proxy (puedes llamarlo "Burp").
    -   Los detalles de la configuración son:
        -   **Host o Dirección IP:** `127.0.0.1`
        -   **Puerto:** `8080`
    -   Ahora puedes activar y desactivar el proxy con un solo clic en el icono de FoxyProxy.

-   **Paso 2: Instalar el Certificado CA de Burp**
    -   Para que Burp pueda "ver" el tráfico cifrado (HTTPS) sin que el navegador muestre errores de seguridad, necesitas que tu navegador confíe en Burp.
    -   **Con Burp ejecutándose y FoxyProxy activado:**
        1.  Navega a la dirección especial: `http://burpsuite`
        2.  Haz clic en el botón "CA Certificate" en la esquina superior derecha para descargar el certificado (un archivo llamado `cacert.der`).
        3.  En Firefox, ve a `Configuración > Privacidad y seguridad > Certificados > Ver certificados...`.
        4.  En la pestaña **"Autoridades"**, haz clic en **"Importar..."**.
        5.  Selecciona el archivo `cacert.der` que descargaste.
        6.  Se abrirá una ventana emergente. Marca la casilla **"Confiar en esta CA para identificar sitios web"** y haz clic en "Aceptar".

### 3. Flujo de Trabajo Básico y Pestañas Esenciales

-   **Target (Objetivo):** A medida que navegas por la aplicación (con el proxy activado), Burp construye automáticamente un mapa del sitio (`Site map`) aquí. Es tu mapa del tesoro, te muestra todas las páginas, scripts y endpoints que has visitado.

-   **Proxy > Intercept (Interceptar):**
    -   Cuando el botón "Intercept is on" está activado, cada petición de tu navegador queda "congelada" en Burp, esperando tu aprobación. Puedes modificarla en tiempo real antes de enviarla al servidor con el botón "Forward".
    -   Para un análisis más cómodo, a menudo se deja en "Intercept is off" y se revisa el historial en la sub-pestaña `HTTP history`.

-   **Proxy > HTTP history (Historial HTTP):**
    -   Aquí se registra cada petición que pasa a través de Burp. Es el lugar perfecto para encontrar una petición interesante que quieras analizar más a fondo.

-   **Repeater (Repetidor): ¡La herramienta más poderosa!**
    -   Desde el historial (o cualquier otro lugar), puedes hacer clic derecho en una petición y seleccionar **"Send to Repeater"**.
    -   La pestaña Repeater te permite tomar esa única petición, modificarla como quieras (cambiar un ID de usuario, intentar una inyección SQL, etc.) y enviarla una y otra vez, viendo la respuesta del servidor al instante. Aquí es donde se realiza la mayor parte del trabajo de búsqueda manual de vulnerabilidades.

### Tu Misión con Burp Suite
1.  Configura Burp Suite con tu navegador.
2.  Lanza OWASP Juice Shop.
3.  Navega por la tienda y observa cómo se construye el mapa del sitio en la pestaña `Target`.
4.  Encuentra una petición interesante en tu historial de `Proxy`, como la que se hace al iniciar sesión o al ver un producto.
5.  Envíala a **Repeater**.
6.  En Repeater, empieza a jugar. ¿Qué pasa si cambias el `id` de un producto en la URL? ¿Qué pasa si introduces una comilla simple (`'`) en un campo de contraseña? Observa las respuestas y busca errores o comportamientos inesperados.