# Ruta de Aprendizaje: Respuesta a Incidentes e Informática Forense (DFIR)

## Introducción
Este ramo es la primera línea de defensa cuando un ataque ya ha ocurrido. El objetivo es aprender a gestionar la crisis (Respuesta a Incidentes) y a investigar el "quién, qué, cuándo, dónde y cómo" del ataque (Informática Forense). El lema aquí es: **"Asumir la brecha"**.

---

### Módulo 1: Fundamentos y Preparación
- [ ] **Tema:** Entender el ciclo de vida de la Respuesta a Incidentes (IR): Preparación, Identificación, Contención, Erradicación, Recuperación y Lecciones Aprendidas.
- [[Ciclo de Vida de la Respuesta a Incidentes.md]]
- [ ] **Tema:** La importancia de la **Cadena de Custodia**. ¿Por qué un mal manejo de la evidencia digital puede invalidar una investigación?
- [[La Importancia de la Cadena de Custodia.md]]
- [ ] **Tema:** Tipos de evidencia digital: Volátil (RAM, caché) vs. No Volátil (Discos duros, SSD).
- [[Tipos de Evidencia Digital.md]]
- [ ] **Actividad:** Leer y analizar un plan de respuesta a incidentes público de una organización.
- [[Actividad - Analizar un Plan de Respuesta a Incidentes.md]]
- [ ] **Herramienta a Explorar:** `FTK Imager Lite`. Aprender a crear una imagen forense de un pendrive (USB).
- [[Herramienta - FTK Imager Lite.md]]

### Módulo 2: Forense de Sistemas de Archivos
- [ ] **Tema:** Análisis de sistemas de archivos Windows (NTFS) y Linux (ext4)
- [[Forense de Sistemas de Archivos.md]]
- [ ] **Tema:** Timestamps (MAC - Modified, Accessed, Created) y cómo delatan la actividad del usuario/atacante.
- [[Análisis de Sistemas de Archivos (NTFS y ext4).md]]] ]
- [ ] **Tema:** Recuperación de archivos eliminados y análisis del espacio no asignado.
- [[Recuperación de Archivos Eliminados y Espacio no Asignado.md]]] ]
- [ ] **Actividad:** Descargar una imagen de disco de un reto forense online (ej. de `digitalcorpora.org`).
- [[Actividad - Descargar Imagen Forense.md]]] ]
- [ ] **Herramienta a Dominar:** `Autopsy`. Cargar la imagen descargada y realizar un análisis básico: buscar palabras clave, revisar la actividad del usuario en el timeline, extraer archivos.
- [[Herramienta a Dominar - Autopsy.md]]

### Módulo 3: Forense de Memoria (RAM)
- [ ] **Tema:** Por qué la memoria RAM es una mina de oro para el investigador (procesos en ejecución, conexiones de red, claves de cifrado, etc.).
- [[Por qué la memoria RAM es una mina de oro.md]]]
- [ ] **Tema:** Proceso de adquisición de memoria de una máquina Windows y Linux.
- [[Adquisición de Memoria (Windows y Linux).md]]
- [ ] **Actividad:** Analizar una imagen de memoria (puedes encontrar ejemplos en la web de Volatility Foundation).
- [[Actividad - Analizar una Imagen de Memoria.md]]Actividad]
- [ ] **Herramienta a Dominar:** `Volatility 3`. Usar plugins básicos para listar procesos (`pslist`), conexiones de red (`netscan`) y extraer historial de comandos (`cmdline`).
- [[Herramienta a Dominar - Volatility 3.md]]

### Módulo 4: Forense de Red y Análisis de Logs
- [ ] **Tema:** Principios del análisis de tráfico de red. Reconstrucción de sesiones y archivos.
- [[Forense de Red y Análisis de Logs.md]] 
- [ ] **Tema:** Identificar Indicadores de Compromiso (IoCs) en logs del sistema operativo, firewall y servidores web.
- [[Principios del Análisis de Tráfico de Red.md]]
- [ ] **Actividad:** Analizar un archivo de captura de paquetes (`.pcap`) de un ataque simulado.
- [[Actividad - Analizar un archivo PCAP.md]] 
- [ ] **Herramienta a Dominar:** `Wireshark`. Aprender a usar filtros para aislar conversaciones y seguir streams TCP/UDP.
- [[Herramienta a Dominar - Wireshark.md]]
- [ ] **Herramienta a Explorar:** Comandos de Kali como `grep`, `awk`, y `sed` para buscar patrones en archivos de log de gran tamaño.
- [[Herramientas a Explorar - grep, awk, sed.md]]

### Proyecto Final Sugerido
- [ ] **Objetivo:** Resolver un reto completo de DFIR de plataformas como `BlueTeams.Academy` o `CyberDefenders`.
- [[Proyecto Final - Reto de DFIR Completo.md]]] ] 
- [ ] **Entregable:** Redactar un informe forense profesional detallando:
    1. Resumen ejecutivo del incidente.
    2. Cronología detallada del ataque (timeline).
    3. Evidencia encontrada para cada paso del ataque.
    4. Indicadores de Compromiso (IoCs) descubiertos.
    5. Recomendaciones para evitar incidentes similares.

