# Diseño de la memoria caché y su gestión

## Introducción

En los sistemas embebidos orientados a IoT, la memoria caché juega un papel fundamental en el rendimiento general del sistema. Debido a que el procesador opera a una velocidad mucho mayor que la memoria principal (RAM), se genera una brecha de rendimiento conocida como *processor-memory gap*. Para reducir este problema, se implementa una jerarquía de memoria donde la caché actúa como una memoria intermedia rápida entre el CPU y la memoria principal.

Según Hennessy y Patterson, la jerarquía de memoria existe porque “las memorias pequeñas y rápidas son costosas, mientras que las memorias grandes y lentas son más económicas”, por lo que se busca combinar ambas para lograr eficiencia y bajo costo. De igual forma, Stallings explica que el principio de localidad (temporal y espacial) permite que la caché funcione de manera efectiva, ya que los programas tienden a reutilizar datos recientemente accedidos o datos cercanos en memoria.

En sistemas IoT, donde el bajo consumo energético y la eficiencia son prioritarios, el diseño de la memoria caché debe ser simple, rápido y con bajo costo de implementación.

---

## Diseño propuesto de memoria caché

Para la arquitectura seleccionada (RISC-V RV32EC), se propone una jerarquía de memoria sencilla y eficiente, adecuada para dispositivos embebidos de bajo consumo.

### Estructura propuesta

### Nivel 1 (L1 Cache)

- Tipo: Caché unificada (instrucciones + datos)
- Tamaño: 16 KB
- Tamaño de bloque: 32 bytes
- Asociatividad: 2-way set associative
- Política de escritura: Write-back
- Política de reemplazo: LRU (Least Recently Used)

### Memoria principal

- Tipo: SRAM / DRAM de bajo consumo
- Tamaño estimado: 256 KB – 512 KB
- Uso principal: almacenamiento de datos permanentes y ejecución del programa

---

## Justificación del diseño

### 1. Caché pequeña para menor consumo energético

Hennessy y Patterson destacan que una caché más pequeña reduce el tiempo de acceso (*hit time*) y disminuye significativamente el consumo de energía. En dispositivos IoT no se requiere una caché grande como en servidores o computadoras de alto rendimiento, sino una solución eficiente para tareas de control, monitoreo y transmisión de datos.

Por ello, una L1 de 16 KB resulta suficiente para cargas ligeras y procesamiento embebido.

---

### 2. Asociatividad de 2 vías

Stallings explica que una caché totalmente directa puede generar demasiados fallos por conflicto (*conflict misses*), mientras que una alta asociatividad aumenta la complejidad y el consumo.

Una caché de 2 vías representa un equilibrio ideal entre rendimiento y simplicidad de hardware, reduciendo conflictos sin elevar demasiado el costo del diseño.

---

### 3. Tamaño de bloque de 32 bytes

El tamaño del bloque afecta directamente el aprovechamiento de la localidad espacial.

Según Patterson y Hennessy, bloques demasiado pequeños desaprovechan accesos cercanos, mientras que bloques demasiado grandes aumentan la penalización por fallo (*miss penalty*).

Por ello, 32 bytes representa una medida eficiente para sistemas embebidos.

---

### 4. Política Write-Back

La política Write-Back reduce la cantidad de escrituras hacia memoria principal, lo cual disminuye el consumo energético y mejora el rendimiento.

Esto resulta especialmente importante en sistemas IoT alimentados por batería, donde cada acceso a memoria externa representa mayor gasto energético.

---

### 5. Política de reemplazo LRU

La política LRU (Least Recently Used) permite reemplazar el bloque menos recientemente utilizado, aprovechando el principio de localidad temporal.

Stallings menciona que esta política mejora la tasa de aciertos (*hit rate*) frente a métodos aleatorios, especialmente en cargas repetitivas típicas de sistemas embebidos.

---

## Gestión de la memoria caché

La gestión de la caché se enfoca en tres aspectos principales:

### Hit y Miss

- Cache Hit: el dato solicitado ya se encuentra en caché y se accede rápidamente.
- Cache Miss: el dato no está en caché y debe buscarse en memoria principal, generando mayor latencia.

El objetivo principal del diseño es aumentar el número de hits y reducir los misses.

---

### Reemplazo de bloques

Cuando la caché está llena y se necesita cargar nueva información, se aplica la política LRU para decidir qué bloque reemplazar.

Esto mejora el rendimiento porque normalmente los datos usados recientemente tienden a reutilizarse.

---

### Escritura de datos

Se utiliza Write-Back, donde las modificaciones primero se realizan en caché y solo se escriben en memoria principal cuando el bloque debe ser reemplazado.

Esto reduce accesos costosos a RAM y mejora la eficiencia energética.

---

## Conclusión

El diseño de memoria caché propuesto busca equilibrar rendimiento, consumo energético y costo de fabricación, factores críticos en sistemas embebidos IoT.

Una caché L1 pequeña, con asociatividad moderada, política Write-Back y reemplazo LRU, permite obtener un sistema eficiente y realista para aplicaciones embebidas modernas.

Siguiendo los principios establecidos por Hennessy & Patterson y Stallings, esta jerarquía de memoria ofrece una solución adecuada para arquitecturas RISC orientadas a dispositivos IoT de bajo consumo.

