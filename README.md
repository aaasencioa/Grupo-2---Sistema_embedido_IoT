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

## Descripción del problema

En el desarrollo de sistemas embebidos orientados al Internet de las Cosas (IoT), una de las principales dificultades no es únicamente construir el dispositivo, sino tomar las decisiones correctas de arquitectura que permitan obtener un sistema eficiente, funcional y sostenible.

Los dispositivos IoT, como sensores inteligentes, relojes digitales, sistemas de monitoreo, dispositivos médicos y automatización industrial, trabajan bajo condiciones muy diferentes a las de una computadora tradicional. Estos sistemas deben operar con bajo consumo de energía, espacio físico reducido, costos de fabricación accesibles y alta confiabilidad, ya que muchos funcionan de manera continua y en entornos críticos.

El verdadero desafío consiste en determinar qué decisiones de diseño son las más adecuadas para cumplir con estas restricciones. Elegir una arquitectura incorrecta puede provocar mayor consumo de batería, menor velocidad de respuesta, aumento de costos o fallos en el funcionamiento del sistema.

Por ello, este proyecto no parte de un problema específico de falla, sino de la necesidad de analizar y justificar cuál es la mejor arquitectura para un sistema embebido IoT, evaluando diferentes alternativas y seleccionando la más eficiente desde el punto de vista técnico y económico.


## Decisiones principales

### 1. Selección de ISA (Instruction Set Architecture)

La primera decisión importante fue seleccionar el tipo de arquitectura de conjunto de instrucciones más adecuada para un sistema embebido IoT.

Se realizó una comparación entre arquitecturas RISC y CISC, analizando aspectos como:

- tipo de instrucciones
- tamaño de instrucciones
- tiempo de ejecución
- acceso a memoria
- consumo energético
- costos de implementación

Después del análisis, se concluyó que la arquitectura RISC es la mejor opción, ya que ofrece instrucciones simples, ejecución rápida y constante, menor complejidad de hardware y mejor eficiencia energética.

Se eligió específicamente la variante RV32EC de RISC-V, porque su extensión “E” reduce la cantidad de registros generales, disminuyendo el tamaño del chip, el consumo de energía y los costos de fabricación. Además, al ser una arquitectura de estándar abierto, elimina costos de licencias.


### 2. Diseño de jerarquía de memoria

La segunda decisión corresponde a la organización de la memoria dentro del sistema.

En dispositivos IoT, el acceso eficiente a la memoria es fundamental para reducir tiempos de respuesta y consumo de energía. Una jerarquía de memoria bien diseñada permite optimizar el uso de caché, memoria principal y almacenamiento, evitando operaciones innecesarias.

Se propone una estructura de memoria enfocada en tareas de control, lectura de sensores y transmisión de datos, priorizando bajo consumo energético y estabilidad operativa antes que alto rendimiento extremo.


### 3. Análisis de rendimiento

La tercera decisión principal fue evaluar si la arquitectura seleccionada realmente ofrece un buen desempeño.

Para ello se utilizaron tres métricas clásicas de arquitectura de computadores:

- CPI (Cycles Per Instruction)
- MIPS (Million Instructions Per Second)
- Ley de Amdahl

Estas métricas permiten medir cuántos ciclos necesita una instrucción, la capacidad de procesamiento del sistema y el impacto real de las optimizaciones realizadas.

El cálculo del CPI promedio dio como resultado 1.7 ciclos por instrucción, lo que representa un rendimiento adecuado para un sistema embebido IoT orientado a eficiencia energética y tareas de control.


## Objetivo del proyecto

Analizar y justificar las decisiones de arquitectura más adecuadas para el diseño de un sistema embebido IoT, considerando restricciones de energía, espacio, costo y rendimiento, con el fin de seleccionar una solución eficiente, escalable y viable para aplicaciones reales.

---
