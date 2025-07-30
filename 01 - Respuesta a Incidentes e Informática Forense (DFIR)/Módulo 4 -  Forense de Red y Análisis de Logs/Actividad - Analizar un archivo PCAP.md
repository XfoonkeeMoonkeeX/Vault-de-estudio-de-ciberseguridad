# 🛠️ Actividad Práctica: Analizar un archivo PCAP

> [!check] Objetivo
> Las capturas de paquetes de tráfico de malware son la mejor manera de aprender. Nos permiten analizar, en un entorno seguro, cómo una infección real ocurre paso a paso.

### 1. Elige tu Recurso

**MALWARE-TRAFFIC-ANALYSIS.NET** es, sin lugar a dudas, uno de los mejores recursos del mundo para esto. Brad Duncan publica regularmente análisis detallados de infecciones de malware, incluyendo los archivos PCAP para que cualquiera los descargue y practique.

-   **Sitio Web:** [https://www.malware-traffic-analysis.net/](https://www.malware-traffic-analysis.net/)

### 2. Descarga la Captura

1.  Ve a la página principal y busca en la sección de "Traffic Analysis Exercises".
2.  Elige un ejercicio. Cada uno presenta un escenario diferente.
3.  Descarga el archivo `.zip` que contiene el PCAP.
4.  **¡MUY IMPORTANTE!** La contraseña para todos los archivos zip del sitio es siempre la misma palabra: **`infected`**.

### 3. Tu Misión

Descomprime el archivo y abre el PCAP con Wireshark. Tu objetivo es reconstruir la cadena de infección (*infection chain*):
1.  **Identifica a la víctima:** ¿Cuál es la dirección IP de la máquina que fue infectada? (Suele ser una IP privada, como `192.168.x.x` o `10.x.x.x`).
2.  **Encuentra el punto de entrada:** ¿Cómo comenzó la infección? ¿Fue un correo electrónico? ¿Una visita a una web comprometida? Filtra por `http` o `dns` para ver qué sitios se visitaron.
3.  **Localiza la descarga del malware:** Sigue los streams HTTP. ¿Puedes encontrar el momento en que se descarga un archivo ejecutable (`.exe`), un `.dll` o un script sospechoso? Intenta exportar ese archivo.
4.  **Detecta la comunicación C2 (Comando y Control):** Después de la infección, el malware "llama a casa". Busca tráfico post-infección que sea repetitivo, que vaya a IPs extrañas o que use protocolos no estándar. Este es el tráfico del C2.
