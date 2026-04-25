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

# Proyecto Final - Arquitectura de Computadoras

## Descripción del problema

El desarrollo de sistemas embebidos orientados al Internet de las Cosas (IoT) requiere tomar decisiones de diseño que permitan optimizar recursos como energía, memoria, rendimiento y costos de fabricación.

A diferencia de una computadora tradicional, los dispositivos IoT operan bajo restricciones más estrictas: deben consumir poca energía, ocupar poco espacio físico, mantener costos accesibles y ofrecer un funcionamiento confiable durante largos periodos de tiempo.

El principal desafío no consiste en resolver una falla específica, sino en determinar qué arquitectura computacional resulta más adecuada para cumplir con estas condiciones. Una mala elección puede generar mayor consumo de batería, menor velocidad de respuesta, mayor costo de producción o menor vida útil del dispositivo.

Por ello, este proyecto se enfoca en analizar y justificar las mejores decisiones de arquitectura para un sistema embebido IoT, evaluando el conjunto de instrucciones (ISA), el diseño de la jerarquía de memoria caché y el análisis de rendimiento del sistema.


## Decisiones principales

### 1. Selección de ISA (Instruction Set Architecture)

Se realizó una comparación entre arquitecturas RISC y CISC para determinar cuál se adapta mejor a sistemas embebidos IoT.

Después del análisis, se concluyó que la arquitectura RISC es la mejor opción debido a su simplicidad, menor consumo energético, rapidez de ejecución y menor complejidad de hardware.

Se seleccionó específicamente la variante RV32EC de RISC-V, ya que su extensión “E” reduce la cantidad de registros generales, disminuyendo el tamaño del chip, el consumo de energía y los costos de fabricación. Además, al ser una arquitectura de estándar abierto, elimina costos de licencias.


### 2. Diseño de la jerarquía de memoria caché

La segunda decisión principal corresponde al diseño de la memoria caché y su jerarquía.

Se propuso una estructura de memoria compuesta por niveles L1, L2 y L3, además de memoria principal y memoria Flash para almacenamiento permanente.

También se definieron políticas de reemplazo y escritura como LRU (Least Recently Used) y Write-Back, permitiendo reducir accesos a memoria principal, mejorar el rendimiento y optimizar el consumo energético.

Esta organización resulta adecuada para sistemas embebidos donde la eficiencia energética y la estabilidad operativa son prioritarias.


### 3. Análisis de rendimiento

La tercera decisión principal fue validar el desempeño de la arquitectura seleccionada mediante métricas clásicas de arquitectura de computadores:

- CPI (Cycles Per Instruction)
- MIPS (Million Instructions Per Second)
- Ley de Amdahl

El cálculo del CPI promedio permitió determinar que cada instrucción requiere en promedio 1.7 ciclos de reloj, lo que representa un rendimiento adecuado para un sistema embebido orientado a tareas de control y eficiencia energética.

Estas métricas permiten comprobar que la arquitectura seleccionada no solo es viable técnicamente, sino también eficiente desde el punto de vista económico y funcional.
