# Problema Teoría. Convocatoria Extraordinaria. Lunes, 17-Junio-2024
* Puntuacion: 10 ptos

### Problema 1 (2.5 ptos): Rendimiento

Nuestro jefe de proyecto nos pide que seleccionemos entre dos procesadores, **P1** y **P2**, para determinar **cuál es el más apropiado** para el proyecto. Disponemos de un **programa de prueba** que realiza ciertos cálculos. Este programa debe tardar como máximo **20 ms** en ejecutarse en el procesador elegido, o de lo contrario no nos servirá. El **60%** de las instrucciones son de multiplicación, y el **40%** restante son de los demás tipos

Los fabricantes de los procesadores P1 y P2 nos proporcionan la siguiente información, relativa a los ciclos que tarda cada tipo de instrucción, y la frecuencia máxima de funcionamiento

| Procesador   |  Multiplicacion | Resto de Instrucciones | Freq    |
|--------------|-----------------|----------------------- |---------|
|P1            |    5 ciclos     |     1 ciclo            | 200 Mhz |
|P2            |    2 ciclos     |     1 ciclo            | 160 Mhz |

Sabemos que el programa de prueba tiene un total de **2 millones de instrucciones**

Se pide:

a) (0.5 ptos) Calcular el CPI del procesador P1 al ejecutar el programa de prueba

b) (0.5 ptos) Calcular el tiempo que tarda P1 en ejecutar el programa de prueba

c) (0.5 ptos) Calcular el CPI del procesador P2 al ejecutar el programa de prueba

d) (0.5 ptos) Calcular el tiempo que tarda P1 en ejecutar el programa de prueba

e) (0.5 ptos) ¿Qué procesador elegirías para el proyecto?

Debes **justificar** TODAS las respuestas


## Solución al problema

**a)** Para obtener el CPI del P1 al ejecutar el programa basta con calcular la media de los ciclos. Sabemos que el 60% de las instrucciones tardan 5 ciclos y que el 40% restante 1 ciclo, en media tardarán:

    CPI1 = 0.6 * 5 + 0.4 * 1 = 3.4

**b)** El tiempo que tarda P1 en ejecutar el programa es su tiempo de CPU. Lo calculamos utilizando la ecuación clásica del rendimiento:

Tcpu1 = (I * CPI1) / F1, siendo I = 2 millones de instrucciones y F1 = 200Mhz
Tcpu1 = (2*10^6 * 3.4) / (200 * 10^6) = 0.034 s = 34 ms

No nos lo piden en este apartado, pero ya vemos que el P1 NO cumple con lo necesario para el proyecto: tarda más de 20 ms en ejecutar el programa. NO nos sirve

**c)** Repetimos los cálculos para P2:

  CPI2 = 0.6 * 2 + 0.4 * 1 = 1.6

**d)** Recalculamos el tiempo de CPU para P2

  Tcpu2 = (I * CPI2) / F2, siendo I = 2 millones de instrucciones y F1 = 160Mhz
  Tcpu2 = (2*10^6 * 1.6) / (160 * 10^6) = 0.02 s = 20 ms
 

**e)** Hay que elegir el **procesador P2**, que es el que cumple con los requisitos pedidos: ejecutar el programa de pruebas en como máximo 20ms. P2 lo hace (aunque por los pelos). El procesador P1 tarda más de 20 ms, por lo que NO nos vale (¡P2, te elijo a tí!)




 

