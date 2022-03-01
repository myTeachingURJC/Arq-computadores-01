# S3: Problema de rendimiento

Las instrucciones de un procesador están divididas en 3 grupos: A, B y C. Tres fabricantes han implementado su propio procesador, usando el mismo repertorio de instrucciones. En esta tabla se muestran los CPI de cada grupo de instrucciones para cada procesador:

| Procesador | Freq (Ghz)| A  |  B  |  C |
|------------|-----------|----|-----|----|
|  P1        | 1         | 1  |  2  |  3 |
|  P2        | 1.5       | 1  |  1  |  3 |
|  P3        | 2.0       | 2  |  3  |  3 |

Para evaluar su rendimiento se ejecuta un programa de prueba que tiene **2 millones de instrucciones**, compuesto de un 20% de instrucciones de tipo A, un 40% de tipo B y un 40% de tipo C

a) ¿Qué procesador tiene mejor rendimiento? (3 ptos)

b) ¿Cuánto mejor es el procesador de mayor rendimiento con respecto a los otros dos? (2 ptos)

## Solución

**a)**  Tendrá mejor rendimiento el procesador que ejecute el programa más rápidamente. Para ello calculamos primero el número de ciclos que tarda cada procesador, y dividimos por su frecuencia

* P1:  Ciclos = N*0.2*1 + N*0.4*2 + N*0.4*3 = N[0.2 + 0.8 + 1.2] = N * 2.2 = 4.4 millones de ciclos
* P2:  Ciclos = N*0.2*1 + N*0.4*1 + N*0.4*3 = N[0.2 + 0.4 + 1.2] = N * 1.8 = 3.6 millones de ciclos
* P3:  Ciclos = N*0.2*2 + N*0.4*3 + N*0.4*3 = N[0.4 + 1.2 + 1.2] = N * 2.8 = 5.6 millones de ciclos

Dividiendo por la frecuencia de cada unos obtenemos el tiempo:

* Tcpu_1 = 4.4*10^6 / 10^9 = 4.4ms
* Tcpu_2 = 3.6*10^6 / 1.5*10^9 = 2.4ms
* Tcpu_3 = 5.6*10^6 / 2*10^9 = 2.8ms

El procesador con mejor rendimiento es el P2

**b)**

* R2 / R1 = Tcpu_1 / Tcpu_2 = 4.4 / 2.4 = 1.83.  **P2 es 1.83 veces más rápido que P1**
* R2 / R3 = Tcpu_3 / Tcpu_2 = 5.6 / 2.4 = 2.33.  **P2 3s 2.33 veces más rápido que P3**

