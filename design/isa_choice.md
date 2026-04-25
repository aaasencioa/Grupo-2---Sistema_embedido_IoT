
# Tabla Comparativa: RISC vs. CISC en IoT

| Característica | RISC (Ej. ARM, RISC-V) | CISC (Ej. Intel, AMD) |
| :--- | :--- | :--- |
| **1. Instrucciones** | Simples: Hacen una sola cosa a la vez. | Complejas: Hacen múltiples cosas a la vez. |
| **2. Tamaño (Longitud)** | Fijo: Todas miden lo mismo (Ej. 32 bits). | Variable: El tamaño cambia según lo que hagan. |
| **3. Tiempo de Ejecución** | Rápido y constante: 1 ciclo de reloj. | Variable: Pueden tomar muchos ciclos de reloj. |
| **4. Acceso a la Memoria** | **Load / Store**: Solo instrucciones específicas pueden leer/escribir en memoria. Los cálculos se hacen en los registros. | **Directo**: Cualquier instrucción matemática puede operar directamente sobre la memoria RAM. |

## Decisión Técnica

Para el desarrollo de sistemas embebidos e IoT, la arquitectura **RISC** es indiscutiblemente la mejor opción debido a las estrictas restricciones físicas de este entorno. Al diseñar dispositivos como sensores de humedad, relojes inteligentes o marcapasos, los tres mayores desafíos a vencer son la falta de energía, el espacio físico reducido y el presupuesto limitado.

Por esta razón, hemos elegido implementar la variante específica **RV32EC**. 

* **Optimización de Hardware:** La extensión "E" (*Embedded*) reduce el número de registros generales de 32 a 16, lo cual disminuye drásticamente el área del chip, optimizando el consumo de batería y los costos de fabricación sin sacrificar el rendimiento en tareas de control.
* **Viabilidad Económica:** Esta decisión técnica viene acompañada de un fuerte respaldo económico: al basarnos en una arquitectura de estándar abierto, eliminamos los gastos de licencias (*royalties*), lo que nos permite reinvertir ese ahorro en componentes de mayor calidad o en reducir el precio final del producto en el mercado.
