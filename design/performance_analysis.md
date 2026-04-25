# Análisis de Rendimiento en Sistemas Embebidos IoT

Un sistema embebido IoT no solo debe ser funcional, sino también eficiente. El análisis de rendimiento es el proceso sistemático para medir, evaluar y optimizar cómo un sistema utiliza sus recursos para cumplir con sus tareas.

Para evaluar el desempeño del sistema embebido IoT, se utilizan tres métricas clásicas de arquitectura de computadores:

1. **CPI (Cycles Per Instruction):** Mide cuántos ciclos de reloj necesita una instrucción, en promedio. Un CPI bajo es vital para reducir el consumo de energía.
2. **MIPS (Million Instructions Per Second):** Mide cuántos millones de instrucciones puede ejecutar el procesador por segundo.
3. **Ley de Amdahl:** Estima el impacto real de optimizar solo una parte del sistema.

---

## 1. Cálculo de CPI (Cycles Per Instruction)

El CPI promedio depende del tipo de instrucciones ejecutadas y de cuántos ciclos requiere cada una.

### Supuestos para la carga de trabajo del sistema IoT:

| Tipo de instrucción | Frecuencia | Ciclos |
| :--- | :--- | :--- |
| Operaciones aritméticas | 50% | 1 |
| Acceso a memoria | 30% | 2 |
| Saltos/Control | 20% | 3 |

### Cálculo:
**CPI = (0.5)(1) + (0.3)(2) + (0.2)(3) = 1.7**

**CPI promedio = 1.7**

### Interpretación
Esto significa que, en promedio, cada instrucción requiere 1.7 ciclos de reloj para completarse. Aunque algunos núcleos como ARM Cortex-M0 pueden acercarse a CPI=1 en condiciones ideales, en cargas reales los accesos a memoria y saltos elevan el valor efectivo.

**Un CPI bajo es deseable porque:**
* Reduce el tiempo de ejecución.
* Disminuye el consumo energético.
* Mejora la capacidad de respuesta en tiempo real.

---

## 2. Cálculo de MIPS (Million Instructions Per Second)

La fórmula utilizada es:
$$MIPS = \frac{Frecuencia (MHz)}{CPI}$$

**Con una frecuencia de 100 MHz:**
$$MIPS = \frac{100}{1.7} \approx 58.8$$

**Resultado: 58.8 MIPS**

### Interpretación
El procesador puede ejecutar aproximadamente 58.8 millones de instrucciones por segundo. Esto es suficiente para tareas típicas de un nodo IoT como:
* Lectura de sensores.
* Filtrado básico de datos.
* Comunicación inalámbrica.
* Respuesta a eventos.

---

## Observaciones Técnicas

* **Limitaciones de MIPS:** MIPS es útil como métrica inicial, pero no debe usarse sola para comparar arquitecturas, ya que distintas arquitecturas (ISA) pueden tener instrucciones de complejidad diferente.
* **Proceso Iterativo:** El análisis de rendimiento en sistemas embebidos IoT es un proceso iterativo. La optimización del firmware y la elección correcta de la arquitectura de hardware son determinantes para la viabilidad comercial, garantizando la longevidad de la batería y la confiabilidad del sistema.
* **Benchmarks adicionales:** Para un análisis más profundo, se recomienda emplear:
    * **Dhrystone (DMIPS)**
    * **CoreMark**

