# 🛠️ Herramienta a Dominar: Autopsy

> [!tool] ¿Qué es?
> Autopsy es una plataforma de análisis forense digital de código abierto y con interfaz gráfica. Es esencialmente una cara amigable para **The Sleuth Kit (TSK)**, una potente colección de herramientas de línea de comandos para el análisis forense.

### 1. Instalación en Kali Linux

Autopsy suele venir preinstalado o está disponible en los repositorios oficiales.
```bash
# Actualiza tus repositorios e instala autopsy
sudo apt update
sudo apt install autopsy
### 2. Flujo de Trabajo Básico de Análisis

**Paso 1: Crear un Nuevo Caso**

- Ejecuta Autopsy.
    
- Selecciona "Create New Case".
    
- Dale un nombre al caso (ej. "M57-Patents Investigation") y elige un directorio base donde se guardarán todos los resultados. Es importante mantener cada caso separado.
    
- Introduce un número de caso y tu nombre como examinador.
    

**Paso 2: Añadir una Fuente de Datos (Data Source)**

- Después de crear el caso, Autopsy te pedirá que añadas una fuente de datos.
    
- Selecciona "Disk Image or VM File" y busca la imagen que descargaste (ej. jo-smith-2009-12-11.E01).
    
- Déjalo en la zona horaria por defecto por ahora (o ajústala si la conoces).
    

**Paso 3: Configurar los Módulos de Ingesta (Ingest Modules)**

- Esta es la fase de análisis automático. Autopsy tiene varios módulos que pueden procesar la imagen. Para un primer análisis, deja los que vienen por defecto activados. Algunos importantes son:
    
    - **Recent Activity:** Extrae la actividad del usuario desde el registro de Windows.
        
    - **Keyword Search:** Busca palabras clave que tú definas.
        
    - **File Type Identification:** Identifica los archivos por su contenido, no por su extensión.
        
    - **Carving:** Realiza el tallado de archivos en el espacio no asignado.
        
- Haz clic en "Next" y deja que Autopsy trabaje. Esto puede tardar mucho tiempo dependiendo del tamaño de la imagen y la potencia de tu máquina.
    

**Paso 4: Explorar la Evidencia**  
Una vez que termine la ingesta, explora los resultados en el panel izquierdo:

- **Data Sources:** Navega por la estructura de archivos como en un explorador normal. Aquí puedes ver archivos borrados (marcados con una 'x' roja).
    
- **Views -> File Types:** Explora los archivos por su tipo (imágenes, videos, documentos). Muy útil para encontrar evidencia específica rápidamente.
    
- **Results -> Extracted Content:** Aquí encontrarás información extraída por los módulos, como historial web, contraseñas guardadas, etc.
    
- **Results -> Keyword Hits:** Si configuraste una búsqueda de palabras clave, aquí aparecerán los resultados.
    
- **Tools -> Timeline:** **¡La herramienta más poderosa!** Haz clic en "Timeline" para ver una representación gráfica de toda la actividad de archivos a lo largo del tiempo. Puedes filtrar por fechas y ver qué hizo el usuario en un momento específico.
    

### Tu Misión en Autopsy

1. Carga la imagen de "Jo Smith".
    
2. Busca archivos eliminados en la sección "Deleted Files".
    
3. Usa la búsqueda de palabras clave para buscar términos relacionados con "patents" (patentes).
    
4. Navega a la sección de "Imágenes y Videos" para ver si hay algo de interés.
    
5. **Abre el Timeline** y examina la actividad en los días cercanos a la fecha de la imagen (2009-12-11). ¿Ves algún pico de actividad inusual?