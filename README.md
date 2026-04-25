## Tema del Proyecto
Sistema Embebido IoT

## Integrantes

- Javier Augusto
- Javier Soberanis
- Marlon
- Cecilia
- Araceli
- Luis Fernando
- Juan
- Lourdes

## Contenido

- Selección de ISA
- Jerarquía de memoria
- Análisis de rendimiento
- Bibliografía en formato APA

## Descripción general del problema

El presente proyecto consiste en el diseño de la arquitectura base de un sistema embebido orientado a aplicaciones de Internet de las Cosas (IoT), considerando las limitaciones reales que presentan este tipo de dispositivos en entornos de producción.

Los sistemas IoT, como sensores de humedad, relojes inteligentes, dispositivos médicos, sistemas de monitoreo remoto y controladores industriales, requieren una arquitectura eficiente que permita operar con bajo consumo energético, tamaño reducido, bajo costo de fabricación y alta confiabilidad.

A diferencia de los computadores tradicionales, los sistemas embebidos trabajan bajo restricciones mucho más estrictas. La batería suele ser limitada, el espacio físico disponible es muy pequeño y los costos deben mantenerse bajos para garantizar competitividad en el mercado. Además, estos dispositivos deben responder rápidamente y funcionar de manera continua, especialmente en aplicaciones críticas como salud, automatización y monitoreo ambiental.

Por ello, el objetivo principal del proyecto es seleccionar una arquitectura computacional adecuada que permita optimizar recursos sin sacrificar rendimiento, estabilidad ni escalabilidad.


## Decisiones principales

### 1. Selección de ISA (Instruction Set Architecture)

Se realizó una comparación entre arquitecturas RISC y CISC para determinar cuál se adapta mejor a sistemas embebidos IoT.

Se concluyó que la arquitectura RISC es la mejor opción debido a su simplicidad, rapidez de ejecución, menor consumo energético y menor complejidad de hardware. Estas características la hacen ideal para dispositivos con recursos limitados.

Se seleccionó específicamente la variante RV32EC de RISC-V, ya que su extensión “E” reduce el número de registros generales de 32 a 16, disminuyendo el área del chip, el consumo de batería y los costos de fabricación.

Además, al ser una arquitectura de estándar abierto, elimina costos de licencias (royalties), permitiendo una solución más económica y flexible.


### 2. Diseño de jerarquía de memoria

La segunda decisión importante corresponde a la organización de la memoria.

En sistemas embebidos IoT, la memoria debe ser eficiente y de bajo consumo. Una memoria caché bien diseñada reduce los accesos frecuentes a la memoria principal, mejorando la velocidad de respuesta y optimizando el uso de energía.

Se propone una jerarquía de memoria orientada a tareas de control, lectura de sensores y transmisión de datos, priorizando eficiencia energética sobre alto rendimiento extremo.


### 3. Análisis de rendimiento

Para validar el diseño, se realizó un análisis de rendimiento utilizando tres métricas clásicas:

- CPI (Cycles Per Instruction)
- MIPS (Million Instructions Per Second)
- Ley de Amdahl
