# Labs Marie Assembler
Los ejercicios incluidos en este repositorio no pretenden ser una copia de los laboratorios ni de tareas similares. Están diseñados como material de apoyo para ayudar a comprender y practicar el lenguaje ensamblador.

A continuación verá alguna información básica para su entendimiento.

### Algunas sentencias básicas:
| Opcode | Instrucción | Address | Descripción                                                                          |
|--------|-------------|---------|--------------------------------------------------------------------------------------|
| 0001   | LOAD        | X       | Carga el contenido de la dirección X en AC.                                          |
| 0010   | STORE       | X       | Almacena el contenido de AC en la dirección X.                                       |
| 0011   | ADD         | X       | Suma el contenido de la dirección X al AC.                                           |
| 0100   | SUB         | X       | Resta el contenido de la dirección X al AC.                                          |
| 0101   | INPUT       | -       | Ingresa un valor desde el teclado al AC.                                             |
| 0110   | OUTPUT      | -       | Muestra el valor de AC en la pantalla.                                               |
| 0111   | HALT        | -       | Termina la ejecución del programa.                                                   |
| 1000   | SKIPCOND    | X       | Salta según condición:<br>000: AC < 0<br>400: AC = 0<br>800: AC > 0<br> (Elemental para bucles)                |
| 1001   | JUMP        | X       | Salta a la dirección X cargándola en el PC.                                          |
| 1010   | LOADI       | X       | Carga el valor inmediato X en el PC.                                                 |
NOTA: PC - Program Counter AC - Acumulador
## Ejemplo:
Imprima los números de 1 hasta n
```
        Input
        Store N				    /Input = N
        LOAD    CERO			/Carga 1 en el AC (contador inicial)
        STORE   COUNTER 		/Guarda el contador en memoria

LOOP,   LOAD COUNTER            /Carga el contador actual
        SUBT N                  /Resta N (COUNTER < N ≡ COUNTER - N < O)
        SKIPCOND 000            /Si Counter(En un inicio 0) < N
        JUMP END                /No se cumple condición
						        /Si se cumple condición
        LOAD COUNTER            /Carga el contador
		ADD ONE                 /Agrega 1
        OUTPUT                  /Imprime el contador en pantalla

        LOAD COUNTER            /Carga el contador nuevamente
        ADD  ONE                /Le suma 1
        STORE COUNTER           /Guarda el nuevo valor del contador

        JUMP LOOP               /Repite el bucle

END,    HALT                    /Fin del programa

/ Derfinición de variables
ONE, 	    DEC 1
COUNTER,    DEC 0
N,		    DEC 10
CERO,	    DEC 0

```
Pruebe su código en [Simulador Marie Assembler](https://marie.js.org/)

Para más información ingrese a [Material Marie](https://github.com/MARIE-js/MARIE.js/wiki)