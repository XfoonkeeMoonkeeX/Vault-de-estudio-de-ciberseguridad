# Tipos de Evidencia Digital: Volátil vs. No Volátil

En la informática forense, la evidencia digital es cualquier información con valor probatorio que se almacena o transmite en formato digital. [2, 5] Comprender la naturaleza de esta evidencia es crucial para una investigación exitosa. La principal clasificación de la evidencia digital se basa en su volatilidad.

---

## Evidencia Volátil

La evidencia volátil es información temporal que se pierde si el dispositivo se apaga o pierde energía. [2, 6] Requiere una fuente de alimentación constante para mantenerse. [6] Por su naturaleza efímera, es fundamental recolectar este tipo de evidencia lo más rápido posible, idealmente mientras el sistema está en funcionamiento. [4]

### Características Principales:
- **Temporal:** Existe solo mientras el sistema está encendido. [2]
- **Dinámica:** Cambia constantemente con la actividad del sistema.
- **Crítica:** A menudo contiene información en tiempo real sobre el estado del sistema, como procesos en ejecución y conexiones de red. [16]

### Ejemplos de Evidencia Volátil:
- **Memoria RAM (Random Access Memory):** Contiene datos sobre programas y procesos en ejecución, conexiones de red activas, usuarios conectados, contraseñas en texto plano, y claves de cifrado. [4, 16]
- **Memoria Caché (CPU Cache):** Almacena datos a los que el procesador necesita acceder rápidamente. [4]
- **Registros del Sistema:** Información de bajo nivel sobre el estado del hardware y el software. [4]
- **Contenido del Portapapeles:** Cualquier información que haya sido copiada. [4]
- **Archivos Temporales del Sistema:** Archivos creados por el sistema operativo o las aplicaciones para un uso a corto plazo. [4]

---

## Evidencia No Volátil

La evidencia no volátil es información que se conserva incluso después de que el dispositivo se apaga. [8] Está almacenada en medios de almacenamiento permanentes. [2]

### Características Principales:
- **Permanente:** No se pierde al cortar la energía. [1, 8]
- **Estática:** No cambia a menos que sea modificada o eliminada intencionadamente.
- **Fuente Primaria:** Generalmente constituye la mayor parte de la evidencia en una investigación.

### Ejemplos de Evidencia No Volátil:
- **Discos Duros (HDD) y Unidades de Estado Sólido (SSD):** Almacenan el sistema operativo, aplicaciones, archivos de usuario, etc. [2, 8]
- **Unidades USB y Tarjetas de Memoria:** Dispositivos de almacenamiento portátiles. [3]
- **CDs, DVDs y Blu-Rays:** Medios ópticos de almacenamiento. [3]
- **Archivos de Registro (Logs):** Registros de eventos del sistema y aplicaciones.
- **Datos en la Nube (Cloud Storage):** Información almacenada en servidores remotos. [2]
- **Archivos de hibernación y de paginación:** Archivos que pueden contener volcados de la memoria RAM.

---

## Importancia en la Investigación Forense

La **volatilidad** de la evidencia dicta el orden en que debe ser recolectada, conocido como el **"Orden de Volatilidad"**. La regla general es recolectar la evidencia más volátil primero, ya que es la que se perderá con mayor facilidad. [20]

1.  **Recolección de Evidencia Volátil (Análisis en Vivo):** Se realiza con el sistema encendido para capturar el estado actual del mismo. Un mal manejo en esta etapa, como apagar el equipo prematuramente, puede destruir evidencia crucial e irrecuperable. [15]
2.  **Recolección de Evidencia No Volátil (Análisis Post-Mortem):** Se realiza después de haber asegurado la evidencia volátil y, por lo general, con el equipo apagado para crear una imagen forense bit a bit del dispositivo de almacenamiento.

El manejo inadecuado de cualquiera de estos tipos de evidencia puede comprometer la **integridad** y **autenticidad** de las pruebas, rompiendo la **Cadena de Custodia** y haciendo que la evidencia sea inadmisible en un tribunal. [14, 15]