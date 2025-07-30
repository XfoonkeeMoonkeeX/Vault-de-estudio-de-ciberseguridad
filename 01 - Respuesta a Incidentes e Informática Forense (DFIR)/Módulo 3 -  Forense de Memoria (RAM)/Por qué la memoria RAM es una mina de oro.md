# Por qué la memoria RAM es una mina de oro

> [!QUOTE] "Apagar la máquina es como dejar que el principal sospechoso se vaya. La evidencia más incriminatoria a menudo desaparece con él."

La memoria de acceso aleatorio (RAM) es **volátil**, lo que significa que su contenido se pierde cuando se corta la energía. Sin embargo, mientras una máquina está en funcionamiento, contiene una instantánea completa de su estado operativo. Para un investigador, esta es una fuente de evidencia irremplazable.

### ¿Qué Evidencia Crítica Encontramos en la RAM?

-   **Procesos en Ejecución:**
    -   Puedes ver cada programa y servicio que se estaba ejecutando en el momento de la captura, incluyendo malware que no deja rastro en el disco duro (malware *sin fichero* o *fileless*).

-   **Conexiones de Red:**
    -   Una lista de todas las conexiones de red activas (TCP/UDP) en el sistema. Puedes ver a qué direcciones IP se estaba conectando una máquina, qué puertos estaba usando y qué proceso era el dueño de esa conexión. Esencial para rastrear la comunicación de un malware con su servidor de Comando y Control (C2).

-   **Credenciales de Usuario:**
    -   La memoria puede contener nombres de usuario y, a veces, contraseñas en texto claro o hashes de contraseñas (ej. de procesos como LSASS en Windows) que un atacante ha capturado o utilizado.

-   **Claves de Cifrado:**
    -   Si un atacante ha cifrado el disco duro con una herramienta como BitLocker o VeraCrypt, la clave de descifrado debe residir en la RAM mientras el sistema está en uso. El análisis de memoria es a menudo la única forma de obtener esta clave y acceder a los datos del disco.

-   **Historial de Comandos:**
    -   Fragmentos de los comandos que un usuario o atacante ha introducido en la consola (CMD, PowerShell, bash).

-   **Contenido no guardado:**
    -   Mensajes de chat, contenido de correos electrónicos, documentos abiertos y cualquier otro dato que una aplicación haya cargado en la memoria pero que aún no se haya guardado en el disco.

La **Orden de Volatilidad** dicta que siempre se debe capturar la evidencia más volátil primero. La memoria RAM está en la cima de esa lista.
