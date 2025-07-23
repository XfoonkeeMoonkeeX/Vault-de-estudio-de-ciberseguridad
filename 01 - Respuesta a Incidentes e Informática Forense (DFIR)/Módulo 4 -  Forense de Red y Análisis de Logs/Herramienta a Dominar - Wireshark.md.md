# 🛠️ Herramienta a Dominar: Wireshark

> [!tool] ¿Qué es?
> Wireshark es el analizador de protocolos de red más popular y potente del mundo. Te permite ver el tráfico de una red a un nivel microscópico. Es una herramienta esencial para cualquier profesional de la ciberseguridad.

### 1. Instalación
Wireshark viene preinstalado en Kali Linux.

### 2. Flujo de Trabajo Básico

**Paso 1: Abrir la Captura**
-   Simplemente abre Wireshark y ve a `File > Open` para cargar tu archivo `.pcap`.

**Paso 2: Entender la Interfaz**
1.  **Lista de Paquetes (Arriba):** Cada línea es un paquete. Verás columnas como Tiempo, IPs de Origen y Destino, Protocolo, etc.
2.  **Detalles del Paquete (Medio):** Al hacer clic en un paquete, esta ventana te muestra una vista desglosada de todas las capas del protocolo (Ethernet, IP, TCP, HTTP, etc.).
3.  **Bytes del Paquete (Abajo):** La representación cruda en hexadecimal y ASCII del paquete.

**Paso 3: Filtrar (La Habilidad Más Importante)**
Ver miles de paquetes es inútil si no puedes encontrar lo que buscas. La barra de "Apply a display filter" es tu mejor amiga.

-   **Filtros Esenciales:**
    -   `ip.addr == 192.168.1.50`: Muestra todo el tráfico desde y hacia esa IP.
    -   `http`: Muestra solo tráfico HTTP.
    -   `dns`: Muestra solo peticiones y respuestas DNS. Es perfecto para ver qué dominios está intentando contactar una máquina.
    -   `tcp.port == 4444`: Muestra tráfico en un puerto específico.
    -   Puedes combinar filtros con `&&` (y), `||` (o): `http && ip.addr == 192.168.1.50`

**Paso 4: Seguir Conversaciones**
Esta es la clave para entender el contexto.
-   Encuentra un paquete que te interese (ej. una petición HTTP GET).
-   Haz clic derecho sobre él.
-   Selecciona **`Follow > TCP Stream`** (o UDP Stream, o HTTP Stream).
-   Se abrirá una nueva ventana mostrando la conversación completa y reensamblada. El texto en rojo es lo que envió un lado, y el texto en azul es lo que respondió el otro. Aquí es donde verás el contenido real.