# Protocolos Comunes de IoT

Los dispositivos IoT suelen ser pequeños, con poca potencia de procesamiento y batería limitada. Por lo tanto, necesitan protocolos de comunicación ligeros y eficientes.

### MQTT (Message Queuing Telemetry Transport)

-   **¿Qué es?** Es el protocolo de mensajería más popular en el mundo del IoT.
-   **Arquitectura:** Se basa en un modelo de **Publicación/Suscripción (Pub/Sub)**.
    1.  **Broker:** Un servidor central que gestiona los mensajes.
    2.  **Publisher (Publicador):** Un dispositivo (ej. un sensor de temperatura) que envía mensajes a un "tópico" (topic) específico en el broker. Un tópico es como un canal, ej. `/casa/sala/temperatura`.
    3.  **Subscriber (Suscriptor):** Un dispositivo (ej. una app en tu móvil) que se suscribe a ese tópico. Cuando el sensor publica un mensaje en el tópico, el broker se lo reenvía inmediatamente a todos los suscriptores.
-   **Características Clave:**
    -   **Ligero:** El encabezado del mensaje es muy pequeño, ideal para redes con poco ancho de banda.
    -   **Asíncrono:** Los dispositivos no necesitan estar conectados al mismo tiempo.
    -   **Calidad de Servicio (QoS):** Permite configurar niveles de garantía de entrega de mensajes.
-   **Seguridad:** Puede (y debe) ser asegurado con TLS para cifrar el tráfico y con autenticación (usuario/contraseña) para controlar quién puede conectarse al broker.

### CoAP (Constrained Application Protocol)

-   **¿Qué es?** Es un protocolo diseñado para ser una especie de "HTTP para dispositivos con restricciones".
-   **Arquitectura:** Se basa en el modelo **Cliente/Servidor** de petición-respuesta, igual que HTTP. Usa los mismos verbos: `GET`, `POST`, `PUT`, `DELETE`.
-   **Características Clave:**
    -   **Ligero:** Funciona sobre UDP, que es más rápido y tiene menos sobrecarga que TCP.
    -   **Síncrono:** La comunicación es directa entre cliente y servidor.
    -   **Descubrimiento de Recursos:** Permite a los clientes descubrir qué recursos (sensores, actuadores) ofrece un servidor.
-   **Seguridad:** La seguridad se implementa a través de DTLS (Datagram Transport Layer Security), que es básicamente TLS para UDP.