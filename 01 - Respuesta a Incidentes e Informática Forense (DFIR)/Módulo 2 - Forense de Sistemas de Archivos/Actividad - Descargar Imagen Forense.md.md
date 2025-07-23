# 🛠️ Actividad Práctica: Descargar una Imagen Forense

> [!check] Objetivo
> Para poder practicar, necesitamos "víctimas". Las imágenes forenses son copias bit a bit de discos duros de escenarios de investigación reales o ficticios. Vamos a descargar una para analizarla con Autopsy.

### 1. Elige tu Recurso

**Digital Corpora** es un archivo público de imágenes de disco para educación e investigación. Es un recurso excelente.

-   **Sitio Web:** [https://digitalcorpora.org/](https://digitalcorpora.org/)

### 2. Descarga la Imagen

Para empezar, una buena imagen es la del escenario **"M57-Patents"**, que es un caso clásico de espionaje corporativo.

1.  Ve a la página de los escenarios: [https://digitalcorpora.org/corpora/scenarios](https://digitalcorpora.org/corpora/scenarios)
2.  Busca y haz clic en el escenario **"The M57-Patents Scenario"**.
3.  Dentro de la descripción, busca la sección de descargas. Encontrarás imágenes de varias máquinas. Una buena para empezar es la de la computadora portátil de "Jo Smith". Busca un archivo con un nombre como `jo-smith-2009-12-11.E01` o similar.
4.  **Descarga el archivo de imagen**. Suelen ser grandes, así que ten paciencia.

### 3. Verifica la Integridad (Paso Crucial)

En el análisis forense, es vital asegurarse de que la evidencia no ha sido alterada. La página de descarga siempre proporciona los **hashes** (MD5 y/o SHA1) del archivo original.

-   Una vez descargada la imagen, abre una terminal en Kali y calcula su hash:
    ```bash
    # Para calcular el hash MD5
    md5sum /ruta/al/archivo/jo-smith-2009-12-11.E01

    # Para calcular el hash SHA1
    sha1sum /ruta/al/archivo/jo-smith-2009-12-11.E01
    ```
-   **Compara el resultado** con el hash que aparece en la página web. Si coinciden, tu copia es perfecta y está lista para ser analizada. Si no, la descarga fue corrupta y debes intentarlo de nuevo.