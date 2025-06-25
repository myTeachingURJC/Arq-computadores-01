# Problema Teoría. Convocatoria Extraordinaria. Lunes, 17-Junio-2024
* Puntuacion: 10 ptos

## Problema 4 (2.5 ptos): Computador nanoRiscV

Tenemos un computador nano-RISCV como el mostrado en la siguiente figura

![](Problema-04-dibujo.png)


El cable de bus **Addr** que conecta con la memoria RAM añade un **retardo de 2ns**, debido a un defecto en su fabricación. En el esquemático se ha indicado con el componente rojo R. Los retardos introducidos por el resto de componentes se describen a continuación:

* **Memoria ROM**: 20ns
* **Memoria RAM**: 8ns de lectura, y 7ns de escritura
* **Fase de decodificación**: Retardo de 6ns
* **Fase de ejecución**: 10ns
* **Fase de Write-back**: 0 ns

El resto de retardos se consideran despreciables (0 ns)

Se pide: 

**a)** (0.5 pto) Calcula el retardo de la fase de Fetch  
**b)** (0.5 pto) Calcula el tiempo que tarda la instrucción `and t0,t1,t2`  
**c)** (0.5 pto) Calcula el tiempo que tarda la instrucción `ld a5,0(zero)`   
**d)** (0.5 pto) Calcula la frecuencia máxima de funcionamiento de este computador  
**e)** (0.5 pto) Si ahora arreglamos el error del cable de manera que no introduzca ningún retraso, ¿Cual sería la nueva frecuencia de funcionamiento?  


# Solución

**a)** Puesto que el retardo del PC es despreciable (0ns), la fase de fetch está determinada por el retardo de la memoria ROM: 20ns

* **Retardo de Fetch**:  **20 ns**

**b)** La instrucción `and` NO accede a memoria por lo que el tiempo de la fase de acceso a memoria es de 0 ns. En la fase de ejecutación tarda 10ms (según especificaciones). Sumando los retardos de todas las fases obtenemos:

* **Retardo de and**: Retardo Fetch + Retardo decodificación + retardo ejecución + retardo acceso memoria + retardo write back = 20 + 6 + 10 + 0 + 0 = 36ns

**c)** La instrucción ld tarda los siguientes tiempos en las fases:

* Fetch: 20
* Decodificación: 6
* Ejecución: 10
* Acceso memoria: 8 (lectura ram) + 2ns (fallo cable) = 10ns
* Write-back: 0ns

El retardo del bus Addr influye sólo en el acceso a memoria, por lo que el retardo es el de la RAM + 2ns = 10ns

* **Retardo de ld**: 20 + 6 + 10 + 10 + 0 = 46ns

**d)** Para calcular la frecuencia máxima de funcionamiento hay que encontrar el caso peor. La fase de Fetch es la misma para todas las instrucciones. El retardo de la decodificación está fijado a 6ns. Y La fase de ejecución a 10.

El caso pero, por tanto, es la instrucción de load (ld), que además de los tiempos anteriores añade el acceso a memoria: 10ns (contando con el fallo del cable)

Por tanto, El periodo mínimo del reloj es de 46ns. Lo que nos da una frecuencia máxima de: 1 / 70ns = **21.7 Mhz (aprox)**

**e)** En este caso se ve afectado sólo el ciclo de acceso a memoria, que pasaría a ser de 8 ns. El caso peor sigue siendo la instrucción de load que ahora tendrá un retardo de 20 + 6 + 10 + 8 + 0 = 44ns.

La nueva frecuencia de funcionamiento es de 1 / 44ns = **22.7 Mhz (aprox)**



