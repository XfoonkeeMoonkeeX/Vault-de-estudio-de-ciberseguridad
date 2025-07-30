# 🛠️ Herramientas a Explorar: grep, awk, sed

> [!tool] ¿Por qué la línea de comandos?
> Los archivos de log pueden tener millones de líneas y pesar gigabytes. Intentar abrirlos con un editor de texto gráfico a menudo bloqueará tu sistema. Las herramientas de línea de comandos de Linux están diseñadas para procesar texto de manera eficiente y rápida, directamente en la terminal.

### `grep`: El Buscador

`grep` (Global Regular Expression Print) busca líneas que contengan un patrón.

-   **Uso Básico:** `grep "palabra_a_buscar" archivo.log`
-   **Comandos Útiles:**
    -   `grep -i "error"`: Busca "error" sin importar si es mayúscula o minúscula.
    -   `grep -v "INFO"`: Invierte la búsqueda, mostrando todas las líneas que **no** contienen "INFO".
    -   `grep -c "Failed password"`: Cuenta el número de líneas que coinciden.
    -   `grep "login" auth.log`: Busca la palabra "login" en el archivo `auth.log`.

### `awk`: El Extractor de Columnas

`awk` es un lenguaje de scripting diseñado para procesar texto basado en columnas.

-   **Uso Básico:** `awk '{print $1, $7}' access.log`
    -   Esto imprimirá la primera (`$1`) y la séptima (`$7`) columna de cada línea del archivo `access.log`. Por ejemplo, la IP del cliente y la URL solicitada.

### `sed`: El Editor de Flujo

`sed` (Stream Editor) se usa para realizar sustituciones o eliminar texto sobre la marcha.

-   **Uso Básico:** `sed 's/Error/FALLO/g' error.log`
    -   Esto reemplazará (`s`) cada ocurrencia de "Error" por "FALLO" en el archivo.

### La Magia de las Tuberías (`|`)

El verdadero poder de estas herramientas se desata cuando las encadenas con el operador "pipe" (`|`). La tubería toma la salida de un comando y la usa como entrada para el siguiente.

-   **Ejemplo Clásico (Analizar logs de un servidor web):**
    > "Quiero saber las 10 direcciones IP que más han accedido a mi página de login."
    ```bash
    # 1. Busca en el log de acceso las líneas que contienen "/login.php"
    # 2. De esas líneas, extrae solo la primera columna (la IP)
    # 3. Ordena las IPs
    # 4. Cuenta cuántas veces aparece cada IP única
    # 5. Ordena el resultado numéricamente en orden inverso (de mayor a menor)
    # 6. Muestra solo las 10 primeras líneas
    grep "/login.php" access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -n 10
    ```
Este tipo de "one-liner" es extremadamente potente para el análisis rápido de logs.
