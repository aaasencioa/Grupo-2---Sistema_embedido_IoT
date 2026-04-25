# Performance Analysis
Siguiendo el enfoque cuantitativo de Hennessy y Patterson, el rendimiento del sistema embebido IoT se evalúa considerando tres factores fundamentales:

- Tiempo de ejecución del CPU
- Impacto de la jerarquía de memoria
- Efecto de mejoras parciales mediante Ley de Amdahl

El objetivo es medir si la arquitectura propuesta satisface requerimientos de desempeño y eficiencia.

## 1. Ecuación de desempeño del CPU

Siguiendo el enfoque cuantitativo de Hennessy y Patterson, el desempeño del procesador puede evaluarse mediante la ecuación clásica de tiempo de CPU:

CPU Time = Instruction Count × CPI × Clock Cycle Time

Donde:

- Instruction Count (IC): número total de instrucciones ejecutadas.
- CPI: ciclos promedio por instrucción.
- Clock Cycle Time: duración de cada ciclo de reloj.

Para el sistema embebido IoT propuesto se asumen los siguientes parámetros:

- 500,000 instrucciones
- CPI base = 1.0
- Frecuencia del procesador = 100 MHz

El tiempo de ciclo se calcula como:

Clock Cycle Time = 1 / (100 × 10^6) = 10 ns

Sustituyendo en la ecuación:

CPU Time = 500000 × 1.0 × 10 ns

CPU Time = 5 ms

Resultado:

El tiempo estimado de ejecución es 5 milisegundos.

Interpretación:

Este resultado representa el tiempo ideal requerido para completar una carga típica del sistema IoT, como lectura de sensores, procesamiento básico y transmisión de datos. Según Hennessy y Patterson, el rendimiento depende de tres variables fundamentales: número de instrucciones, CPI y velocidad de reloj, por lo que cualquier optimización debe enfocarse en reducir una o más de estas.

---

## 2. CPI real considerando stalls

El libro distingue entre un CPI ideal y un CPI real afectado por interrupciones del pipeline (stalls). Para modelarlo se utiliza:

Pipeline CPI = Ideal CPI + Structural Stalls + Data Stalls + Control Stalls

Supuestos:

- Ideal CPI = 1.0
- Structural stalls = 0.1
- Data stalls = 0.4
- Control stalls = 0.2

Entonces:

CPI = 1.0 + 0.1 + 0.4 + 0.2

CPI = 1.7

Resultado:

CPI efectivo = 1.7

Interpretación:

Aunque idealmente el procesador ejecutaría una instrucción por ciclo, en la práctica existen penalizaciones causadas por:

- Dependencias entre instrucciones.
- Accesos a memoria.
- Saltos condicionales.
- Riesgos estructurales del pipeline.

Estas penalizaciones elevan el CPI real y reducen el rendimiento. Hennessy y Patterson destacan que este análisis es clave para evaluar Instruction-Level Parallelism (ILP) y comprender cuellos de botella en arquitecturas modernas.

---

## 3. Impacto de memoria (AMAT)

La jerarquía de memoria también afecta el rendimiento. Para medirlo se utiliza Average Memory Access Time (AMAT):

AMAT = Hit Time + (Miss Rate × Miss Penalty)

Supuestos:

- Hit Time = 1 ciclo
- Miss Rate = 5%
- Miss Penalty = 20 ciclos

Sustituyendo:

AMAT = 1 + (0.05 × 20)

AMAT = 2 ciclos

Resultado:

Tiempo promedio de acceso a memoria = 2 ciclos

Interpretación:

Aunque la caché permite accesos rápidos, los fallos de caché incrementan el tiempo efectivo de acceso. Esto impacta directamente el CPI, ya que cada fallo introduce ciclos adicionales de espera.

En sistemas embebidos IoT esto es particularmente importante porque:

- La memoria suele ser limitada.
- La latencia puede afectar respuesta en tiempo real.
- Fallos frecuentes incrementan consumo energético.

De acuerdo con Hennessy y Patterson, reducir el Miss Rate o Miss Penalty puede producir mejoras significativas en desempeño global.
