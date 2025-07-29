# Ruta de Aprendizaje: Seguridad IoT / OT

## Introducción
Este ramo se adentra en la seguridad de dos mundos convergentes y de alto impacto: el Internet de las Cosas (IoT), que nos rodea en casa y ciudades, y la Tecnología Operacional (OT), que controla infraestructuras críticas (electricidad, agua, fábricas). El lema aquí es: **"La seguridad va más allá de la pantalla"**.

---

### Módulo 1: Fundamentos y Diferencias Clave
- [ ] **Tema:** IT vs. OT vs. IoT. ¿Por qué la prioridad en OT/IoT suele ser Disponibilidad > Integridad > Confidencialidad? (El modelo CIA invertido).
- [[IT vs. OT vs. IoT.md]]
- [ ] **Tema:** El Modelo Purdue de arquitectura de redes de control industrial. Entender la segmentación.
- [[El Modelo Purdue.md]]
- [ ] **Tema:** Protocolos comunes de IoT: `MQTT`, `CoAP`.
- [[Protocolos Comunes de IoT.md]]
- [ ] **Tema:** Protocolos comunes de OT: `Modbus`, `DNP3`.
- [[Protocolos Comunes de OT.md]]
- [ ] **Actividad:** Elegir un dispositivo IoT de tu casa (Smart TV, cámara, enchufe) e investigar su arquitectura y los protocolos que usa.
- [[Actividad - Investigar un Dispositivo IoT Doméstico.md]] 

### Módulo 2: Superficie de Ataque en IoT
[[Superficie de Ataque en IoT.md]]
- [ ] **Tema:** Vulnerabilidades comunes en dispositivos IoT: contraseñas por defecto, interfaces web inseguras, falta de cifrado, actualizaciones inexistentes.
- [[Vulnerabilidades Comunes en Dispositivos IoT.md]]
- [ ] **Tema:** Extracción y análisis de firmware. Búsqueda de secretos y vulnerabilidades en el código del dispositivo.
- [[Extracción y Análisis de Firmware.md]]
- [ ] **Actividad:** Descargar el firmware de un router o dispositivo IoT desde la web del fabricante.
- [[Actividad - Descargar Firmware de un Dispositivo.md]]
- [ ] **Herramienta a Dominar:** `binwalk`. Usarlo para intentar extraer el sistema de archivos del firmware descargado.
- [[Herramienta a Dominar - binwalk.md]]
- [ ] **Herramienta a Explorar:** `Shodan.io`. Aprender a buscar dispositivos IoT expuestos en internet.
- [[Herramienta a Explorar - Shodan.io.md]]

### Módulo 3: Amenazas y Seguridad en Entornos OT/ICS
[[Amenazas y Seguridad en OT.md]]
- [ ] **Tema:** Componentes de un Sistema de Control Industrial (ICS): PLC, HMI, SCADA.
- [[Componentes de un Sistema de Control Industrial (ICS).md]]
- [ ] **Tema:** Estudio de casos de ataques a OT: Stuxnet, TRITON, CrashOverride. Entender las tácticas, técnicas y procedimientos (TTPs).
- [[Estudio de Casos de Ataques a OT.md]]
- [ ] **Actividad:** Investigar y mapear uno de estos ataques usando el framework `MITRE ATT&CK for ICS`.
- [[Actividad Práctica, Mapear un Ataque con MITRE ATT&CK for ICS .md]]
- [ ] **Tema:** Seguridad física y de red en entornos industriales: segmentación, firewalls, diodos de datos.
- [[Seguridad Física y de Red en Entornos Industriales.md]]

### Módulo 4: Aseguramiento y Estándares
[[Aseguramiento y Estándares.md]]
- [ ] **Tema:** El estándar `ISA/IEC 62443` como marco de referencia para la seguridad en OT.
- [[Estándar ISA-IEC 62443.md]]
- [ ] **Tema:** Monitoreo de seguridad en redes OT: ¿Por qué el escaneo activo puede ser peligroso? Enfoque en el monitoreo pasivo.
- [[Monitoreo de Seguridad en Redes OT.md]]
- [ ] **Tema:** El desafío del "legacy": cómo proteger sistemas que tienen décadas de antigüedad y no pueden ser actualizados.
- [[El Desafío del Legacy.md]]
- [ ] **Actividad:** Diseñar un diagrama de red simple para una pequeña planta de manufactura, aplicando los conceptos de segmentación del Modelo Purdue.
- [[Actividad - Diseñar Diagrama de Red de una Planta.md]] 

### Proyecto Final Sugerido
- [ ] **Objetivo:** Realizar una evaluación de riesgos de seguridad para un sistema ciberfísico.
- [[Proyecto Final - Evaluación de Riesgos de un Sistema Ciberfísico.md]]
- [ ] **Entregable:** Elegir un sistema (ej. un sistema de riego inteligente para agricultura o el sistema de control de climatización de un edificio) y entregar un informe que detalle:
    1. Identificación de activos críticos.
    2. Análisis de amenazas y vulnerabilidades específicas del sistema.
    3. Evaluación del impacto potencial (operacional, financiero, de seguridad física).
    4. Recomendaciones de controles de seguridad (técnicos y de procedimiento) basados en ISA/IEC 62443.
     [[El Entregable.md]]
