# Problema Teoría. Convocatoria Extraordinaria. Lunes, 17-Junio-2024
* Puntuacion: 10 ptos

### Problema 2 (2.5 ptos): Ordenacion/alineamiento/direccionamiento

Tenemos un computador de 32-bits que dispone de 8 registros de propósito general (t0-t7). La anchura de la memoria es de 32-bits.  La ordenación que usa es **Little-endian**. Para acceder a los datos de la memoria utiliza un direccionamiento **directo**. Puede acceder tanto a datos alineados como no alineados. Estas son algunas de las instrucciones disponibles:

* `lb rd, dir`: Leer el byte que hay en la dirección dir y guardarlo en el registro rd
* `lh rd, dir`: Leer la media palabra que hay en la dirección dir y guardarla en el registro rd
* `lw rd, dir`: Leer la palabra que hay en la dirección dir y guardarla en el registro rd

Este es el contenido de la memoria, a partir de la dirección 0xA0000000. Todos los valores están en hexadecimal

| Dirección      | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|----------------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0xA0000000     |00 |11 | 22|33 |44 |55 |66 | 77| 88| 99| AA| BB|CC |DD |EE | FF|
| 0xA0000010     |40 |50 | 60|70 |80 |90 |A0 | B0| C0| D0| E0| F0|10 |20 |30 | 40| 


Resuelve los siguientes apartados, calculando el resultado y justificando cómo lo has obtenido

**a)** (0.5 ptos) Indica el valor de los registros t1 y t2 al ejecutar estas instrucciones

```asm
lb t1, 0xA000000A
lb t2, 0xA000001A
```

**b)** (0.5 ptos) Indica el valor de los registros t3 y t4 al ejecutar estas instrucciones

```asm
lh t3, 0xA00000000
lh t4, 0xA00000010
```

**c)** (0.5 ptos) Indica el valor de los registros t5 y t6 al ejecutar estas instrucciones

```asm
lw t5, 0xA00000000
lw t6, 0xA0000000E
```

**d)** (0.5 ptos) Indica el número de accesos a memoria de esta instrucción para leer el dato

```asm
lb t1, 0xA000000A
```

**e)** (0.5 ptos) Indica el número de accesos a memoria de esta instrucción para leer el dato

```asm
lw t6, 0xA0000000E
```


# Solución

**a)**

En ambas instrucciones se lee un byte, por lo que no afecta el tipo de ordenación. Los valores de los registros son:

* t1 = 0xAA (Byte en la posición 0xA000000A)
* t2 = 0xE0 (Byte en la posicion 0xA000001A)

**b)** 

En estas instrucciones se leen medias palabras (2 bytes), por lo que la ordenación sí afecta. Como es Little endian, el byte situado en la dirección menor será el de menor peso

* t3 = 0x1100 (Media palabra a partir de la dirección 0xA0000000, con ordenación little endian)
* t4 = 0x5040 (Media palabra a partir de la dirección 0xA0000010, con ordenación little endian)

**c)**

En estas instrucciones se leen palabras (4 bytes), por lo que la ordenación sí afecta. Como es Little endian, el byte situado en la dirección menor será el de menor peso

* t5 = 0x33221100 (Palabra a partir de la dirección 0xA0000000, con ordenación little endian)
* t6 = 0x5040FFEE (Palabra a partir de la dirección 0xA000000E, con ordenación little endian)

**d)**  

Como se trata de la lectura de 1 byte, el concepto de alineación no afecta. Sólo se necesita 1 acceso para leer este byte

**e)**

La instrucción lee una palabra (4 bytes). Pero como la dirección NO está alineada, hay que realizar 2 accesos a memoria. Uno para leer la palabra situada en la dirección alineada anterior (0xA00000C), y otro para leer la palabra en la dirección alineada posterior (0xA0000010)

