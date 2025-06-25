# Problema Teoría. Convocatoria Extraordinaria. Lunes, 17-Junio-2024
* Puntuacion: 10 ptos

### Problema 2 (2.5 ptos): Ordenacion/alineamiento/direccionamiento

Tenemos un computador de 32-bits que dispone de 8 registros de propósito general (a0-a7). La anchura de la memoria es de 32-bits.  La ordenación que usa es **Little-endian**. Para acceder a los datos de la memoria utiliza un direccionamiento **directo**. Puede acceder tanto a datos alineados como no alineados. Estas son algunas de las instrucciones disponibles:

* `lb rd, dir`: Leer el byte que hay en la dirección dir y guardarlo en el registro rd
* `lh rd, dir`: Leer la media palabra que hay en la dirección dir y guardarla en el registro rd
* `lw rd, dir`: Leer la palabra que hay en la dirección dir y guardarla en el registro rd

Este es el contenido de la memoria, a partir de la dirección 0xF000F000. Todos los valores están en hexadecimal

| Dirección      | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | A | B | C | D | E | F |
|----------------|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0xF000F000     |10 |21 | 32|43 |54 |65 |76 | 87| 98| A9| BA| CB|DC |ED |FE | 0F|
| 0xF000F010     |50 |60 | 70|80 |90 |A0 |B0 | C0| D0| E0| F0| 00|20 |30 |40 | 50| 


Resuelve los siguientes apartados, calculando el resultado y justificando cómo lo has obtenido

**a)** (0.5 ptos) Indica el valor de los registros a1 y a2 al ejecutar estas instrucciones

```asm
lb a1, 0xF000F00A
lb a2, 0xF000F01A
```

**b)** (0.5 ptos) Indica el valor de los registros a3 y a4 al ejecutar estas instrucciones

```asm
lh a3, 0xF0000F000
lh a4, 0xF0000F010
```

**c)** (0.5 ptos) Indica el valor de los registros a5 y a6 al ejecutar estas instrucciones

```asm
lw a5, 0xF0000F000
lw a6, 0xF0000F00E
```

**d)** (0.5 ptos) Indica el número de accesos a memoria de esta instrucción para leer el dato

```asm
lb a1, 0xF000F00A
```

**e)** (0.5 ptos) Indica el número de accesos a memoria de esta instrucción para leer el dato

```asm
lw a6, 0xF0000F00E
```


# Solución

**a)**

En ambas instrucciones se lee un byte, por lo que no afecta el tipo de ordenación. Los valores de los registros son:

* a1 = 0xBA (Byte en la posición 0xF000F00A)
* a2 = 0xF0 (Byte en la posicion 0xF000F01A)

**b)** 

En estas instrucciones se leen medias palabras (2 bytes), por lo que la ordenación sí afecta. Como es Little endian, el byte situado en la dirección menor será el de menor peso

* a3 = 0x2110 (Media palabra a partir de la dirección 0xF000F000, con ordenación little endian)
* a4 = 0x6050 (Media palabra a partir de la dirección 0xF000F010, con ordenación little endian)

**c)**

En estas instrucciones se leen palabras (4 bytes), por lo que la ordenación sí afecta. Como es Little endian, el byte situado en la dirección menor será el de menor peso

* a5 = 0x43322110 (Palabra a partir de la dirección 0xF000F000, con ordenación little endian)
* a6 = 0x60500FFE (Palabra a partir de la dirección 0xF000F00E, con ordenación little endian)

**d)**  

Como se trata de la lectura de 1 byte, el concepto de alineación no afecta. Sólo se necesita 1 acceso para leer este byte

**e)**

La instrucción lee una palabra (4 bytes). Pero como la dirección NO está alineada, hay que realizar 2 accesos a memoria. Uno para leer la palabra situada en la dirección alineada anterior (0xF000F00C), y otro para leer la palabra en la dirección alineada posterior (0xF000F010)

