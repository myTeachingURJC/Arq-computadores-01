# Problema Teoría. Convocatoria Extraordinaria. Martes, 17-Junio-2024
* Puntuacion: 10 ptos

## Problema 3 (2.5 ptos): Electrónica digital

Tenemos el siguiente circuito digital

![](Problema-03-dibujo.png)

Responde a las siguientes preguntas:

**a)** (0.5 ptos) Indica cuál es la parte combinacional de este circuito y qué retardo tiene

**b)** (0.5 ptos) Indica cuál es la parte secuencial de este circuito y qué retardo tiene

**c)** (0.5 ptos) Indica el retardo total del circuito completo

**d)** (0.5 ptos) Calcula la frecuencia máxima de funcionamiento de este circuito

**e)** (0.5 ptos) Si inicialmente el registro tiene un valor de 3, y la señal `write` tiene un valor de 1 (ciclo 0), indica el valor de la señal `Q` durante los 3 siguientes ciclos de reloj (ciclos 1, 2 y 3)


# Solución

**a)** Este cicuito está formado por dos elementos: un registro de 8 bits (secuencial) y un sumador de 2 operandos de 8 bits (combinacional). La parte combinacional es este circuito sumador, que tiene un retardo de 4 ns

**b)** La parte secuencial del circuito es el registro de 8 bits, que tiene un retardo de 8 ns

**c)** Se trata de la conexión en cascada de un circuito secuencial con otro combinacional, por tanto el retardo total es la suma de ambos retardos: 8 ns + 4 ns = 12 ns

**d)** La frecuencia máxima de este circuito es la inversa del retardo mínimo del circuito, calculado en el apartado anterior. Fmax = 1 / Tmin = 1 / 12 ns = 83.3 Mhz (aprox.)

**e)** En el ciclo 0, la señal Q vale 1, y el valor el registro es de 3 (situación inicial).  El valor en el siguiente ciclo (ciclo 1) será el valor del contador en el ciclo 0 (0) al que se le suma 3. Como write está a '1', este valor se captura en el siguiente ciclo. Esto se repite en el resto de ciclos obteniéndose una de cuenta de 3 en 3: 3, 6, 9, 12...

Por tanto, en los ciclos 1,2 y 3, el valor de out será de 6, 9 y 12 respectivamente



