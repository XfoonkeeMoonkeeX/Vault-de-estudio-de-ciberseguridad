# 🛠️ Actividad Práctica: Descargar Firmware de un Dispositivo

> [!check] Objetivo
> Obtener una muestra de firmware de un dispositivo del mundo real para poder analizarla en la siguiente actividad con `binwalk`.

### 1. Elige tu Objetivo

Necesitas encontrar un fabricante que ofrezca públicamente las actualizaciones de firmware para sus dispositivos. Los fabricantes de routers son la mejor opción para esto.

-   **Marcas Sugeridas:**
    -   TP-Link
    -   D-Link
    -   Netgear
    -   Linksys
    -   ASUS

### 2. El Proceso de Búsqueda y Descarga

1.  **Ve al sitio web del fabricante.** Busca la sección de "Soporte" (Support) o "Descargas" (Downloads).
2.  **Busca un modelo de producto específico.** No importa si no tienes el router físicamente. Simplemente elige un modelo de la lista, por ejemplo, `TP-Link Archer C7` o `D-Link DIR-816`.
3.  **Navega a la sección de Firmware.** Los sitios de soporte suelen tener pestañas para "Manuales", "Drivers" y "Firmware". Haz clic en esta última.
4.  **Descarga el archivo de firmware.** Generalmente será un archivo `.zip` que contiene un archivo `.bin` en su interior. Descarga la versión más reciente disponible.
5.  **Crea una carpeta de trabajo.** En tu máquina Kali, crea una nueva carpeta para este proyecto (ej. `~/iot_firmware_analysis`) y guarda el archivo `.bin` dentro de ella.

### Ejemplo de Búsqueda

Imaginemos que elegimos el router **D-Link DIR-867**.

1.  Buscamos en Google: `D-Link DIR-867 support`
2.  Vamos a la página de soporte oficial de D-Link para ese modelo.
3.  Hacemos clic en la pestaña "Firmware".
4.  Descargamos el archivo `DIR-867_A1_FW_1.30B03.zip`.
5.  Descomprimimos el .zip y guardamos el archivo `.bin` que contiene en nuestra carpeta de trabajo.

Ya tienes tu "cerebro digital" listo para la autopsia.
