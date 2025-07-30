# La Ecuación del Riesgo

> [!QUOTE] "El riesgo no es una certeza, es una posibilidad calculada. La gestión de riesgos es el arte de gestionar esas posibilidades."

El concepto fundamental que sustenta toda la gestión de riesgos en ciberseguridad (y en cualquier otro campo) se puede simplificar en una fórmula conceptual:

`Riesgo = Probabilidad x Impacto`

Desglosemos los componentes:

### Probabilidad (Likelihood)

-   **¿Qué es?** Es la **posibilidad** de que una amenaza específica explote con éxito una vulnerabilidad. No es una ciencia exacta, sino una estimación.
-   **Factores que influyen en la probabilidad:**
    -   **Nivel de la Amenaza:** ¿Es un atacante poco cualificado o un estado-nación?
    -   **Nivel de la Vulnerabilidad:** ¿Es una vulnerabilidad fácil de explotar o requiere condiciones muy específicas?
    -   **Controles de Seguridad Existentes:** ¿Tenemos firewalls, EDR, 2FA? Cada control reduce la probabilidad de éxito del atacante.
-   **Ejemplo:** La probabilidad de que un atacante explote una vulnerabilidad crítica en un servidor web expuesto a internet que no tiene parches es **alta**. La probabilidad de que un atacante explote esa misma vulnerabilidad en un servidor aislado en una red interna es **baja**.

### Impacto (Impact)

-   **¿Qué es?** Es el **daño** o las consecuencias negativas para la organización si el riesgo se materializa (es decir, si el ataque tiene éxito).
-   **Factores que influyen en el impacto:**
    -   **Criticidad del Activo:** No es lo mismo que se comprometa un servidor de pruebas a que se comprometa la base de datos de clientes.
    -   **Tipo de Daño:** El impacto puede ser:
        -   **Financiero:** Pérdida de ingresos, multas regulatorias (GDPR, etc.), costes de remediación.
        -   **Operacional:** Interrupción del negocio, detención de la producción.
        -   **Reputacional:** Pérdida de confianza de los clientes, daño a la marca.
        -   **De Seguridad Física:** Daños a la propiedad o, en el peor de los casos, a la vida humana (en entornos OT).
-   **Ejemplo:** El impacto de un ataque de ransomware en el servidor de archivos de un hospital es **crítico**, porque afecta directamente la capacidad de tratar a los pacientes (impacto operacional y de seguridad física).

> [!check] Conclusión
> Un riesgo alto no viene solo de una alta probabilidad o de un alto impacto. El mayor riesgo se encuentra en la intersección de ambos: una vulnerabilidad fácil de explotar en un sistema muy crítico. **El objetivo de la ciberseguridad es reducir la probabilidad a través de controles, y reducir el impacto a través de la resiliencia y planes de respuesta.**
