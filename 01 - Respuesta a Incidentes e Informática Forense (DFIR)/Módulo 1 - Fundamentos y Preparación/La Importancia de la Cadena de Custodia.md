# Tema: La Importancia de la Cadena de Custodia

## Introducción: La Evidencia en el Mundo Físico

Imagina una escena del crimen en el mundo real. Un detective encuentra una pistola. No la recoge con la mano desnuda. Usa guantes, la coloca en una bolsa de evidencia sellada, firma la bolsa, anota la hora y el lugar, y la transporta a un laboratorio. Cada persona que abre esa bolsa para analizar el arma debe registrar su nombre, la fecha y el motivo.

Este proceso es la **Cadena de Custodia**. Es la bitácora ininterrumpida que documenta la vida completa de una prueba, desde su descubrimiento hasta su presentación en un tribunal.

---

## ¿Qué es la Cadena de Custodia en el Mundo Digital?

En informática forense, el concepto es idéntico, pero la "evidencia" es mucho más frágil. Una Cadena de Custodia digital es **el registro cronológico y meticuloso que demuestra que la evidencia digital no ha sido alterada o manipulada en ninguna etapa del proceso de investigación.**

Responde a estas preguntas cruciales para cada pieza de evidencia (un disco duro, un pendrive, una imagen de memoria, un archivo de log):

-   **Quién** la recolectó y la ha manejado.
-   **Qué** es exactamente la evidencia.
-   **Cuándo** fue recolectada y manejada.
-   **Dónde** fue recolectada y dónde ha estado almacenada.
-   **Por qué** se accedió a ella en cada paso.
-   **Cómo** fue manejada (ej. se creó una imagen, se transportó, etc.).

---

## ¿Por qué un Mal Manejo Invalida una Investigación?

Esta es la pregunta central. Una Cadena de Custodia rota o inexistente destruye una investigación por tres razones fundamentales:

### 1. **Pérdida de Admisibilidad Legal**

Este es el golpe mortal. Si el caso llega a un tribunal, el abogado de la parte contraria no atacará tu análisis técnico; atacará tu **procedimiento**. Su trabajo es crear **duda razonable**.

*   **Pregunta del Abogado:** *"¿Puede usted garantizar al 100% que nadie alteró este disco duro entre que lo encontró y lo analizó? ¿No? ¿Entonces cómo podemos fiarnos de que los archivos que nos muestra no fueron plantados o modificados después del hecho?"*

Si tu Cadena de Custodia tiene "agujeros" (tiempo sin registrar, firmas faltantes, un manejo inadecuado), la evidencia se considera contaminada. Un juez puede declararla **inadmisible**, y es como si nunca la hubieras encontrado.

### 2. **Pérdida de [[Integridad de la Evidencia]]**

La evidencia digital es increíblemente sensible. Un simple acto como conectar un disco duro sospechoso a tu máquina de Windows sin las precauciones adecuadas puede alterar miles de archivos y metadatos (timestamps, logs, etc.).

Una Cadena de Custodia rota implica que no puedes probar que la evidencia es una réplica exacta de su estado original. Si no puedes probar la integridad, tus conclusiones son, en el mejor de los casos, suposiciones.

**El "Sello Digital": El Hashing**
Aquí es donde el [[Hashing]] (SHA-256, MD5) se vuelve vital. Un hash es una huella digital única para un conjunto de datos.
*   **Procedimiento Correcto:** Se calcula el hash de la evidencia original en el momento de la recolección. Cada vez que se trabaja con una copia, se vuelve a calcular su hash. Si los hashes coinciden, se prueba que la copia es idéntica al original.
*   **Procedimiento Incorrecto:** Si no se calcula el hash al principio, o si se trabaja directamente sobre la evidencia original, es imposible demostrar que no la has alterado, ni siquiera accidentalmente.

### 3. **Pérdida de Credibilidad del Investigador**

Incluso si el caso no llega a un tribunal, una mala gestión de la evidencia destruye tu credibilidad profesional. Si presentas un informe a la dirección de una empresa para justificar el despido de un empleado, pero tu proceso fue descuidado, la decisión puede ser cuestionada o incluso revertida.

Una Cadena de Custodia sólida demuestra que eres un profesional meticuloso, objetivo y que sigue estándares reconocidos por la industria.

---

### Escenario Práctico: El Desastre Evitable

| Acción | ❌ **Manejo Incorrecto (Cadena Rota)** | ✅ **Manejo Correcto (Cadena Sólida)** |
| :--- | :--- | :--- |
| **Descubrimiento** | Un analista encuentra un portátil sospechoso. Lo toma y lo lleva a su escritorio. | El analista documenta la ubicación, fecha, hora. Toma fotografías. Usa guantes y coloca el portátil en una bolsa antiestática sellada. Rellena una etiqueta de evidencia. |
| **Transporte** | El portátil queda en su coche mientras va a almorzar. | El portátil se transporta directamente a un laboratorio seguro. Se firma un formulario de recepción. |
| **Análisis** | Enciende el portátil para "echar un vistazo". Lo conecta a la red de la oficina. | Crea una [[Imagen Forense]] bit a bit del disco duro usando un bloqueador de escritura. Calcula el hash del original y de la imagen. **Trabaja siempre sobre la imagen, nunca sobre el original.** |
| **Almacenamiento** | El portátil original queda sobre un escritorio en un área abierta. | La evidencia original se almacena en un armario de evidencia cerrado y con acceso restringido. Se documenta quién tiene la llave. |

### Conclusión

La Cadena de Custodia no es burocracia; es el **pilar científico** del análisis forense. Garantiza que la evidencia que presentas es la misma que encontraste, sin alteraciones ni contaminaciones. Sin ella, no estás haciendo ciencia forense, solo estás mirando archivos.
