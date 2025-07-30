# El Desafío del "Legacy": Protegiendo el Pasado en el Presente

> [!QUOTE] "El mayor desafío de la seguridad OT no es proteger el futuro, es asegurar sistemas diseñados antes de que la ciberseguridad fuera siquiera una palabra."

Los sistemas "legacy" (heredados) son dispositivos y software que siguen siendo operativos y funcionales, pero que son antiguos, no tienen soporte y, a menudo, corren en sistemas operativos obsoletos como Windows XP o Windows 2000.

### ¿Por qué Existen Tantos Sistemas Legacy en OT?

-   **Ciclos de Vida Largos:** Un PLC o un sistema HMI está diseñado para funcionar durante 20, 30 o incluso 40 años. A diferencia del mundo de IT donde los servidores se reemplazan cada 3-5 años.
-   **Coste de Actualización:** Reemplazar un sistema de control puede costar millones y requerir parar la producción durante semanas. Si el sistema "funciona", no hay un incentivo económico para cambiarlo.
-   **Certificación y Validación:** Los sistemas en industrias como la farmacéutica o la nuclear pasan por procesos de validación muy rigurosos. Cualquier cambio, incluso un parche de seguridad, requeriría un costoso proceso de re-validación.
-   **"Si no está roto, no lo arregles":** Es la mentalidad predominante en muchos entornos industriales.

### Estrategias para Proteger Sistemas Legacy

Ya que no podemos "parchear" o "arreglar" el sistema en sí mismo, debemos protegerlo desde fuera, como si pusiéramos un tesoro frágil dentro de una caja fuerte moderna.

1.  **Aislamiento y Segmentación (Virtual Patching):**
    -   Esta es la defensa más importante. El sistema legacy debe estar en su propia zona de red ultra-restringida.
    -   Se usa un firewall industrial o un sistema de prevención de intrusiones (IPS) delante del dispositivo legacy. Este firewall actúa como un "parche virtual": se configura para bloquear todo el tráfico malicioso conocido que podría afectar al sistema vulnerable, impidiendo que el ataque llegue a su objetivo.

2.  **Endurecimiento de los Nodos Adyacentes:**
    -   Si el sistema legacy (ej. una HMI en Windows XP) necesita comunicarse con otro sistema (ej. un servidor de historial en Windows Server 2019), ese sistema moderno debe estar completamente parcheado y "endurecido" (hardened).

3.  **Monitoreo de Red Estricto:**
    -   Implementar monitoreo pasivo en el segmento de red donde vive el sistema legacy para detectar inmediatamente cualquier comunicación anómala hacia o desde él.

4.  **Control de Aplicaciones (Application Whitelisting):**
    -   En la propia máquina legacy (si es posible), instalar software que impida que se ejecute cualquier programa que no esté en una lista blanca pre-aprobada. Esto previene la ejecución de malware si un atacante lograra colocarlo en la máquina.
