
---

### **6. Nota para la Herramienta**

**Nombre de archivo:** `Herramienta a Dominar - Burp Suite.md`
_(Crea una nueva nota con este nombre y pega el siguiente contenido)_

```markdown
# 🛠️ Herramienta a Dominar: Burp Suite Community Edition

> [!tool] ¿Qué es?
> Burp Suite es tu navaja suiza para el hacking web. Es un proxy que se sienta entre tu navegador y el servidor, permitiéndote ver, modificar y repetir cada petición.

### 1. Lanzamiento
Burp Suite ya viene instalado en Kali Linux. Búscalo en el menú de aplicaciones (`ZAP & BurpSuite`).

### 2. Configuración del Proxy
-   La forma más fácil es usar la extensión de navegador **FoxyProxy**. Instálala en Firefox.
-   Configura FoxyProxy para que envíe el tráfico a Burp, que por defecto escucha en `127.0.0.1` puerto `8080`.

### 3. Instalar el Certificado de Burp
Para que Burp pueda "ver" el tráfico HTTPS sin errores, tu navegador necesita confiar en él.
-   Con Burp y el proxy activados, ve a `http://burpsuite`.
-   Haz clic en "CA Certificate" para descargar el certificado.
-   En las configuraciones de Firefox, ve a "Privacidad y Seguridad" -> "Certificados" -> "Ver certificados" -> "Autoridades" -> "Importar" y selecciona el archivo que descargaste. Marca la casilla **"Confiar en esta CA para identificar sitios web"**.

### 4. Flujo de Trabajo Básico
1.  Activa el proxy en FoxyProxy.
2.  En la pestaña "Proxy" -> "Intercept" de Burp, activa **"Intercept is on"**.
3.  Navega a una página en Juice Shop. La petición quedará "atrapada" en Burp.
4.  Haz clic derecho en la petición y elige **"Send to Repeater"**.
5.  En la pestaña "Repeater", puedes modificar la petición (ej. cambiar un ID de usuario) y darle a "Send" para ver la respuesta del servidor una y otra vez. **¡Aquí es donde ocurre la magia!**