
---

### **4. Nota para la Actividad Práctica**

**Nombre de archivo:** `Actividad - Analizar una Imagen de Memoria.md`
_(Crea una nueva nota con este nombre y pega el siguiente contenido)_

```markdown
# 🛠️ Actividad Práctica: Analizar una Imagen de Memoria

> [!check] Objetivo
> Al igual que con el forense de disco, necesitamos muestras para practicar. La Volatility Foundation proporciona imágenes de memoria de diferentes sistemas operativos y escenarios de ataque.

### 1. Elige tu Recurso

La **Volatility Foundation Wiki** es el mejor lugar para encontrar imágenes de memoria públicas y seguras para practicar.

-   **Sitio Web de Muestras:** [https://github.com/volatilityfoundation/volatility/wiki/Memory-Samples](https://github.com/volatilityfoundation/volatility/wiki/Memory-Samples)

### 2. Descarga la Imagen

Para un primer análisis, una imagen de Windows 7 es ideal porque es un sistema muy bien soportado por Volatility y lleno de artefactos fáciles de encontrar.

1.  Ve a la página de muestras.
2.  Busca la sección "Windows". Una buena opción es el reto **"BlackEnergy APT"** o el más sencillo **"Practical Malware Analysis"**.
3.  Descarga el archivo. Suelen estar en formato `.zip` o `.rar`, y dentro encontrarás la imagen de memoria, que a menudo tiene una extensión `.vmem`.
4.  **Descomprime el archivo** en una carpeta de trabajo en tu máquina Kali.

### 3. Verifica la Integridad (Opcional pero Recomendado)

Si la página proporciona un hash para la imagen, es una buena práctica verificarlo para asegurarte de que tu copia es idéntica a la original.
```bash
# Navega a la carpeta donde descomprimiste el archivo
cd /ruta/a/la/carpeta_de_trabajo

# Calcula el hash (ej. md5)
md5sum nombre_de_la_imagen.vmem
```
Compara el resultado con el proporcionado en la web.
```

---

### **5. Nota para la Herramienta**

**Nombre de archivo:** `Herramienta a Dominar - Volatility 3.md`
_(Crea una nueva nota con este nombre y pega el siguiente contenido)_

```markdown
# 🛠️ Herramienta a Dominar: Volatility 3

> [!tool] ¿Qué es?
> Volatility es el framework de código abierto más avanzado y reconocido a nivel mundial para el análisis de memoria volátil. Es una herramienta de línea de comandos escrita en Python que permite extraer artefactos forenses de volcados de RAM.

### 1. Instalación en Kali Linux

Volatility 3 se puede instalar fácilmente usando el gestor de paquetes de Python, `pip`.

```bash
# Actualiza el sistema
sudo apt update

# Instala pip y las dependencias de Volatility
sudo apt install -y python3 python3-pip

# Instala Volatility 3
pip install volatility3
```
*Nota: Después de la instalación, el ejecutable puede llamarse `vol.py` o `volatility`. Para estar seguros, usaremos la ruta completa en los ejemplos.*

### 2. Flujo de Trabajo Básico de Análisis

Volatility funciona a través de **plugins**. Tú le dices a Volatility dónde está la imagen de memoria y qué plugin (qué tipo de información) quieres extraer.

**Paso 0: Identificar el Perfil del Sistema (¡Crucial!)**
Antes de nada, necesitas saber qué sistema operativo contenía esa memoria. Volatility 3 intenta hacer esto automáticamente, pero el primer comando siempre debería ser para confirmarlo.

-   **Comando:**
    ```bash
    # La sintaxis es: python3 /path/to/vol.py -f /ruta/a/la/imagen.vmem <plugin>
    # La ruta a vol.py tras instalar con pip suele ser /usr/local/bin/vol.py
    python3 /usr/local/bin/vol.py -f /ruta/a/tu/imagen.vmem windows.info.Info
    ```
-   **Resultado:** Este comando te dará información sobre el perfil sugerido del sistema operativo (ej. `Win7SP1x64`), la fecha de la imagen, etc.

**Paso 1: Listar Procesos en Ejecución (`pslist`)**
Este es el "hola mundo" del forense de memoria. Muestra todos los procesos que estaban activos.

-   **Comando:**
    ```bash
    python3 /usr/local/bin/vol.py -f /ruta/a/tu/imagen.vmem windows.pslist.PsList
    ```
-   **Qué buscar:** Procesos con nombres sospechosos, procesos sin un proceso padre, o procesos ejecutándose desde rutas inusuales (ej. `/tmp` o `C:\Users\...\AppData\Local\Temp`).

**Paso 2: Revisar Conexiones de Red (`netscan`)**
Muestra las conexiones de red activas en el momento del volcado.

-   **Comando:**
    ```bash
    python3 /usr/local/bin/vol.py -f /ruta/a/tu/imagen.vmem windows.netscan.NetScan
    ```
-   **Qué buscar:** Conexiones a direcciones IP extrañas o conocidas por ser maliciosas, o procesos como `svchost.exe` haciendo conexiones a puertos no estándar.

**Paso 3: Extraer Historial de Comandos (`cmdline`)**
Muestra los argumentos de la línea de comandos con los que se lanzó cada proceso.

-   **Comando:**
    ```bash
    python3 /usr/local/bin/vol.py -f /ruta/a/tu/imagen.vmem windows.cmdline.CmdLine
    ```
-   **Qué buscar:** Es muy útil para ver si un atacante lanzó comandos a través de `cmd.exe` o `powershell.exe`, revelando exactamente qué intentaba hacer.

### Tu Misión en Volatility
1.  Descarga una imagen de memoria de la web de Volatility.
2.  Usa el plugin `windows.info.Info` para identificar el sistema operativo.
3.  Usa `windows.pslist.PsList` y revisa la lista de procesos. ¿Hay alguno que te parezca extraño?
4.  Usa `windows.netscan.NetScan`. ¿Ves alguna conexión de red interesante?
5.  Usa `windows.cmdline.CmdLine`. ¿Puedes ver cómo se iniciaron algunos de los procesos?
```
