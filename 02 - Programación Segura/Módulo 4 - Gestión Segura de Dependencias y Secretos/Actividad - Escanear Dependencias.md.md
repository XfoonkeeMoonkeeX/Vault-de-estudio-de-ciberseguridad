# 🛠️ Actividad Práctica: Escanear las Dependencias de un Proyecto

> [!check] Objetivo
> Utilizar herramientas de SCA estándar para encontrar vulnerabilidades conocidas en las dependencias de un proyecto de ejemplo.

### Escenario 1: Proyecto JavaScript/Node.js

**1. Prepara el Proyecto:**
Crea una carpeta nueva y dentro de ella un archivo `package.json` con una dependencia antigua y vulnerable. Por ejemplo, una versión vieja de la librería `express`.
```json
// package.json
{
  "name": "proyecto-vulnerable",
  "version": "1.0.0",
  "dependencies": {
    "express": "4.16.3" 
  }
}

**2. Instala las Dependencias:**  
Abre una terminal en esa carpeta y ejecuta:

Generated bash      `npm install`
    
**3. Audita el Proyecto:**  
Usa la herramienta de auditoría integrada de npm.

Generated bash      `npm audit`
    
**4. Analiza el Resultado:**  
npm audit te mostrará una tabla con las vulnerabilidades encontradas, su severidad (low, moderate, high, critical), una descripción y la dependencia vulnerable (que podría ser una dependencia transitiva).

**5. Intenta la Remediación Automática:**  
npm audit a menudo puede solucionar los problemas automáticamente actualizando las versiones de los paquetes de forma segura.

Generated bash      `npm audit fix`
    
---

### Escenario 2: Proyecto Python

**1. Prepara el Proyecto:**  
Crea una carpeta nueva y dentro un archivo requirements.txt con una dependencia vulnerable. Por ejemplo, una versión antigua de la librería requests.

Generated # requirements.txt      `requests==2.19.0`


**2. Instala las Dependencias y la Herramienta de Auditoría:**  
Abre una terminal, crea un entorno virtual (recomendado) e instala todo.

Generated bash      `python3 -m venv venv source venv/bin/activate pip install -r requirements.txt pip install pip-audit`
    
**3. Audita el Proyecto:**  
Ejecuta pip-audit.

Generated bash      `pip-audit`
    
**4. Analiza el Resultado:**  
De forma similar a npm, pip-audit te informará sobre las dependencias vulnerables encontradas y te dará un enlace al CVE o la descripción del problema. La solución manual generalmente implica actualizar la versión de la librería en tu archivo requirements.txt a una versión segura y volver a instalar.