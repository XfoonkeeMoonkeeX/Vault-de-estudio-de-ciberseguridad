# 🛠️ Herramienta a Dominar: Sysmon

> [!tool] ¿Qué es?
> Sysmon (System Monitor) es una herramienta gratuita de la suite **Sysinternals** de Microsoft (creada por Mark Russinovich). Una vez instalado, se ejecuta como un servicio y un driver en segundo plano, y enriquece drásticamente los logs de eventos de Windows con **telemetría de seguridad de alta calidad**. No previene ataques, pero los hace increíblemente visibles. Es, posiblemente, la herramienta gratuita más importante para un Threat Hunter en un entorno Windows.

### ¿Qué Hace que Sysmon sea tan Especial?

Los logs de eventos por defecto de Windows son buenos, pero tienen puntos ciegos. Sysmon los llena. Por ejemplo:
-   El Evento de creación de proceso nativo de Windows (ID 4688) no registra el hash del proceso. **Sysmon (Event ID 1) sí lo hace.**
-   Windows no registra de forma nativa las conexiones de red por proceso. **Sysmon (Event ID 3) sí lo hace.**
-   Windows no registra la creación de archivos. **Sysmon (Event ID 11) sí lo hace.**

### Eventos Clave de Sysmon para un Hunter

Sysmon genera muchos tipos de eventos. Estos son algunos de los más importantes:
-   **Event ID 1: Process Creation.** El más importante. Registra la ejecución de cada proceso, su hash, la línea de comandos completa y el proceso padre.
-   **Event ID 3: Network Connection.** Registra cada conexión de red saliente, incluyendo el proceso que la inició, las IPs y puertos de origen y destino.
-   **Event ID 7: Image Loaded.** Registra la carga de DLLs por parte de un proceso. Útil para detectar técnicas de DLL injection.
-   **Event ID 8: CreateRemoteThread.** Detecta cuando un proceso crea un hilo en otro proceso, la técnica principal usada por el malware para inyectar código.
-   **Event ID 11: FileCreate.** Registra la creación de archivos. Muy útil para ver cuándo un malware se escribe en el disco.
-   **Event ID 12, 13, 14: Registry Events.** Registran la creación, modificación y borrado de claves de registro, esencial para cazar técnicas de persistencia.
-   **Event ID 22: DNSEvent.** Registra todas las consultas DNS realizadas por cada proceso.

---

### 🛠️ Actividad Práctica: Instalación y Configuración

**1. Descarga los Materiales:**
-   **Sysmon:** Descárgalo desde la página oficial de Microsoft Sysinternals.
-   **Configuración:** Sysmon sin una buena configuración puede ser muy ruidoso. Usaremos una configuración popular y muy robusta creada por **SwiftOnSecurity**. Descarga el archivo `sysmonconfig-export.xml` desde su repositorio de GitHub: [https://github.com/SwiftOnSecurity/sysmon-config](https://github.com/SwiftOnSecurity/sysmon-config)

**2. Instalación en una VM de Windows:**
-   Crea una máquina virtual de Windows (Windows 10 o Server) para no afectar a tu sistema principal.
-   Copia el ejecutable de Sysmon (`Sysmon64.exe` o `Sysmon.exe`) y el archivo de configuración (`sysmonconfig-export.xml`) a la VM.

**3. Proceso de Instalación (desde una terminal de Administrador):**
-   Abre `cmd.exe` o `PowerShell` **como Administrador**.
-   Navega a la carpeta donde guardaste los archivos.
-   Ejecuta el siguiente comando para instalar Sysmon con el archivo de configuración:
    ```powershell
    # Si estás en la misma carpeta que los archivos
    .\Sysmon64.exe -accepteula -i .\sysmonconfig-export.xml
    ```

**4. Verifica la Instalación:**
-   Sysmon se instala como un servicio. Puedes verificar que está corriendo en `services.msc`.
-   Abre el **Visor de Eventos** (`Event Viewer`).
-   Navega a `Applications and Services Logs / Microsoft / Windows / Sysmon / Operational`.
-   **Aquí es donde vivirán todos los logs de Sysmon.** Ya deberías ver eventos apareciendo.

**5. Genera Actividad y Observa:**
-   Realiza algunas acciones simples en tu VM:
    -   Abre el navegador.
    -   Abre la calculadora (`calc.exe`).
    -   Abre una terminal (`cmd.exe`) y ejecuta un comando como `ping 8.8.8.8`.
-   Refresca el log de Sysmon en el Visor de Eventos.
-   **Tu Misión:**
    -   Busca el **Event ID 1** para la ejecución de `ping.exe`. ¿Puedes ver cuál fue el proceso padre? ¿Y la línea de comandos completa?
    -   Busca el **Event ID 3** para la conexión de red de `ping.exe`. ¿Puedes ver la dirección IP de destino?
    -   Busca el **Event ID 22** para la consulta DNS. ¿Qué proceso realizó una consulta para `google.com` cuando abriste el navegador?

Esta actividad te dará una apreciación inmediata de la increíble visibilidad que Sysmon proporciona.