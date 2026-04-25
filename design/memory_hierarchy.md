# Diseño de la memoria caché y su gestión

## Introducción

En los sistemas embbedidos orientados a IoT, la memoria caché es fundamental para mejorar el rendimiento del procesador y reducir el consumo energético. Debido a que la velocidad del CPU es mucho mayor que la velocidad de acceso a la memoria principal, se genera una diferencia de rendimiento conocida como *processor-memory gap*.

Para solucionar este problema se implementa una jerarquía de memoria, donde las memorias más pequeñas y rápidas se ubican más cerca del procesador, mientras que las memorias más grandes y lentas se utilizan para almacenamiento principal.

Según Hennessy y Patterson, esta organización permite equilibrar velocidad, costo y capacidad. Stallings también explica que el principio de localidad temporal y espacial justifica el uso de memoria caché, ya que los programas suelen reutilizar datos recientes o acceder a posiciones cercanas de memoria.

En dispositivos IoT, donde el bajo consumo y el espacio reducido son prioritarios, la jerarquía de memoria debe diseñarse de forma eficiente y simple.

# Jerarquía de memoria propuesta

Para la arquitectura seleccionada RISC-V RV32EC, se propone la siguiente jerarquía de memoria:

| Nivel | Tipo | Tamaño | Función principal |
|---|---|---:|---|
| L1 | Caché primaria | 16 KB | Acceso inmediato del CPU |
| L2 | Caché secundaria | 64 KB | Reduce accesos a memoria principal |
| L3 | Caché terciaria | 256 KB | Soporte adicional para cargas mayores |
| RAM | Memoria principal | 512 KB | Ejecución general del sistema |
| Flash | Almacenamiento permanente | 2 MB | Firmware y datos persistentes |


# Diseño de cada nivel de caché

## Caché L1 (Nivel 1)

### Características

- Tipo: Caché unificada (instrucciones + datos)
- Tamaño: 16 KB
- Tamaño de bloque: 32 bytes
- Asociatividad: 2-way set associative
- Política de escritura: Write-Back
- Política de reemplazo: LRU (Least Recently Used)

### Justificación

La caché L1 debe ser pequeña y extremadamente rápida, ya que es la primera memoria consultada por el procesador.

Hennessy y Patterson indican que una caché pequeña reduce el *hit time* y mejora la eficiencia energética. Para sistemas IoT no se requiere una caché grande, sino una respuesta rápida con bajo consumo.

## Caché L2 (Nivel 2)

### Características

- Tipo: Caché secundaria
- Tamaño: 64 KB
- Tamaño de bloque: 64 bytes
- Asociatividad: 4-way set associative
- Política de escritura: Write-Back
- Política de reemplazo: LRU

### Justificación

La L2 actúa como respaldo cuando ocurre un fallo en L1 (*cache miss*). Su objetivo es evitar accesos frecuentes a RAM, los cuales consumen más energía y tiempo.

Stallings explica que una mayor asociatividad en L2 ayuda a reducir los *conflict misses* sin generar excesiva complejidad.

## Caché L3 (Nivel 3)

### Características

- Tipo: Caché compartida de respaldo
- Tamaño: 256 KB
- Tamaño de bloque: 64 bytes
- Asociatividad: 8-way set associative
- Política de escritura: Write-Back
- Política de reemplazo: Pseudo-LRU

### Justificación

Aunque muchos sistemas embebidos pequeños no implementan L3, en aplicaciones IoT más complejas puede utilizarse como un nivel adicional para mejorar la estabilidad del sistema y reducir aún más el acceso a memoria principal.

La política Pseudo-LRU reduce el costo de implementación frente a un LRU completo.

# Gestión de la memoria caché

## Cache Hit y Cache Miss

### Cache Hit

Ocurre cuando el dato solicitado ya se encuentra en la caché.

Resultado:

- acceso rápido
- menor consumo energético
- mejor rendimiento

### Cache Miss

Ocurre cuando el dato no está en la caché y debe buscarse en un nivel inferior (L2, L3 o RAM).

Resultado:

- mayor latencia
- mayor consumo
- menor rendimiento

El objetivo principal del diseño es maximizar los hits y minimizar los misses.


## Política de reemplazo

Cuando la caché está llena y se necesita almacenar nueva información, se debe reemplazar un bloque existente.

### Política utilizada: LRU

LRU (Least Recently Used) reemplaza el bloque menos recientemente utilizado.

Esto aprovecha la localidad temporal, ya que normalmente los datos usados recientemente tienen mayor probabilidad de volver a utilizarse.

Según Stallings, esta política mejora considerablemente la tasa de aciertos.



## Política de escritura

### Política utilizada: Write-Back

Con Write-Back, los cambios primero se realizan en caché y solo se escriben en memoria principal cuando el bloque necesita ser reemplazado.

Ventajas:

- menos accesos a RAM
- menor consumo energético
- mejor rendimiento

Esto resulta ideal para sistemas IoT alimentados por batería.


# Conclusión

La jerarquía de memoria propuesta busca equilibrar velocidad, consumo energético y costos de fabricación, factores críticos en sistemas embebidos IoT.

Una estructura con L1 pequeña y rápida, L2 de respaldo eficiente y L3 opcional para mayor estabilidad permite optimizar el rendimiento sin sacrificar eficiencia energética.

Siguiendo los principios establecidos por Hennessy & Patterson y Stallings, este diseño resulta adecuado para arquitecturas RISC orientadas a sistemas embebidos modernos.


