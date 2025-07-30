# Componentes de un Sistema de Control Industrial (ICS)

> [!QUOTE] "Entender los componentes de un ICS es como aprender la anatomía de un ser vivo. Cada órgano tiene una función específica y vital."

Un Sistema de Control Industrial (ICS) no es una sola cosa, sino un conjunto de componentes que trabajan juntos para automatizar un proceso industrial. Estos son los tres más importantes.

### PLC (Programmable Logic Controller)
*Controlador Lógico Programable*

-   **¿Qué es?** Es el "cerebro" a nivel de campo. Un PLC es un ordenador industrial robusto y en tiempo real diseñado para automatizar procesos electromecánicos.
-   **Función:** Lee entradas de sensores (Nivel 0 del Modelo Purdue), ejecuta un programa con una lógica predefinida (ej. "si la presión supera X, abre la válvula Y") y escribe salidas a actuadores (Nivel 0).
-   **Ubicación:** Generalmente en el **Nivel 1** del Modelo Purdue, cerca del proceso físico que controla.
-   **Características:** Son extremadamente fiables y están diseñados para operar durante años sin interrupción en condiciones ambientales hostiles (vibraciones, temperaturas extremas).

### HMI (Human-Machine Interface)
*Interfaz Hombre-Máquina*

-   **¿Qué es?** Es la "cara" del proceso. Una HMI es una pantalla gráfica (a menudo táctil) que permite a un operador humano supervisar e interactuar con los PLCs y el proceso.
-   **Función:** Muestra datos del proceso en tiempo real (temperaturas, presiones, alarmas) y permite al operador enviar comandos (ej. encender una bomba, cambiar un punto de ajuste).
-   **Ubicación:** Generalmente en el **Nivel 2** del Modelo Purdue, en la sala de control del área.
-   **Importancia en Seguridad:** Una HMI comprometida puede permitir a un atacante enviar comandos maliciosos al proceso o mostrar información falsa al operador para ocultar un ataque.

### SCADA (Supervisory Control and Data Acquisition)
*Control y Adquisición de Datos Supervisado*

-   **¿Qué es?** SCADA no es un solo dispositivo, sino un **sistema** que permite la supervisión y el control a gran escala, a menudo sobre grandes distancias geográficas.
-   **Función:** SCADA es el sistema que agrupa la información de múltiples PLCs y HMIs. Permite un control centralizado de toda una planta o incluso de una infraestructura distribuida como una red eléctrica o un oleoducto.
-   **Componentes:** Un sistema SCADA incluye:
    -   **Servidores SCADA (MTU - Master Terminal Unit):** El servidor central que se comunica con los dispositivos de campo.
    -   **Unidades Terminales Remotas (RTU):** Dispositivos de campo (similares a los PLCs) que recopilan datos.
    -   **Red de Comunicación:** La infraestructura de red que los conecta (radio, satélite, fibra).
    -   **HMIs centralizadas.**
-   **Ubicación:** Los servidores SCADA y las HMIs centrales residen en el **Nivel 3** del Modelo Purdue.
