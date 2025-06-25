# Problema Teoría. Convocatoria Extraordinaria. Martes, 17-Junio-2024
* Puntuacion: 10 ptos

### Problema 1 (2.5 ptos): Rendimiento

Una empresa quiere mejorar el rendimiento de una aplicación robótica, que se ejecuta en  un computador empotrado con procesador RISCV que funciona a la frecuencia de 1Ghz.

Por especificaciones de la empresa, el computador no se puede cambiar. Por tanto, habrá que mejorar el rendimiento cambiando el compilador. Para ello vamos a evaluar los compiladores A y B

El fabricante del procesador nos proporciona información sobre los CPIs de las instrucciones, que se dividen en 3 grupos: Instrucciones de tipo 1, 2 y 3

| Instrucción  | CPI |
|--------------|-----|
| Tipo 1       | 1.2 |
| Tipo 2       | 2   |
| Tipo 3       | 1   |

La aplicación se compila con ambos compiladoras A y B. En esta tabla se resume el resultado de los programas ejecutables generados con cada compilador, desglosados en sus tipos de instrucciones

| Compilador |  Instrucciones totales |  Tipo 1  |  Tipo 2  |  Tipo 3 |
|------------|------------------------|----------|----------|---------|
| A          |  5000                  |  1500    | 1500     | 2000    |
| B          |  6000                  |  1200    | 1800     | 3000    |

Se pide:

**a)** (0.5 pto). ¿Cuantos ciclos tarda en ejecutarse la aplicación cuando se usa el compilador A?
**b)** (0.5 pto). ¿Cuanto tiempo tarda la aplicación cuando se usa el compilador A?
**c)** (0.5 pto). ¿Cuantos ciclos tarda en ejecutarse la aplicación cuando se usa el compilador B?
**d)** (0.5 pto). ¿Cuanto tiempo tarda la aplicación cuando se usa el compilador B?
**e)** (0.5 pto). Calcula el rendimiento relativo. ¿Qué compilador elegirías?

**NOTA**: Justifica todas las respuestas, indicando las ecuaciones y razonamiento usados

### Solución al problema

**a)** (0.5 pto). ¿Cuantos ciclos tarda en ejecutarse la aplicación cuando se usa el compilador A?

Cada grupo de instrucción de un tipo dado tardará en total: I * CPI ciclos. Sumando todos los ciclos obtenemos el total:

Ciclos totales = ciclos instrucciones tipo 1 + ciclos instrucciones tipo 2 + ciclos instrucciones tipo 3 =  
I1 * CPI1 + I2 * CPI2 + I3 * CPI3 = 1500 * 1.2 + 1500 * 2 + 2000 * 1 = 6800 Ciclos

La aplicación tarda **6800 ciclos** cuando se usa el compilador A

**b)** (0.5 pto). ¿Cuanto tiempo tarda la aplicación cuando se usa el compilador A?

La frecuencia del procesador es F = 1Ghz

El tiempo será: Tcpu = Ciclos / F = 6800 / 1Ghz = 6800 ns = 6.8µs

La aplicación tarda **6.8µs** en ejecutarse cuando se usa el compilador A

**c)** (0.5 pto). ¿Cuantos ciclos tarda en ejecutarse la aplicación cuando se usa el compilador B?

El cálculo es el mismo que para el apartado 1:

Ciclos totales = 1200 * 1.2 + 1800 * 2 + 3000 * 1 = 8040 Ciclos

La aplicación tarda **8040 ciclos** cuando se usa el compilador B

**d)** (0.5 pto). ¿Cuanto tiempo tarda la aplicación cuando se usa el compilador B?

Tcpu = Ciclos / F = 8040 / 1 Ghz = 8040 ns = 8.04µs

**e)** (0.5 pto). Calcula el rendimiento relativo. ¿Qué compilador elegirías?

Rendimiento relativo n = Rendimiento A / Rendimiento B = 8.04µs / 6.8µs =  1.18 (aprox)

El compilador A genera un código que es **1.18 veces más rápido** que el generado por el compilador B. Por tanto, **elegiría el Compilador A**

