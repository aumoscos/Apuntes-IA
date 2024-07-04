## Introducción a las [[Redes neuronales]]

**1**

![[Pasted image 20240604113049.png]]
![[Pasted image 20240604113119.png]]
La neurona envía la misma salida a todas las neuronas conectadas a su salida.
$x_0$ siempre es igual a 1, dado que en la ecuación se tiene $w_0$, osea que su coeficiente es 1.

### Funciones de Transferencia
![[Pasted image 20240604113209.png]]
Hardline (Hard Limitator)

2

Hardlines (Symetric hard limitator)


3

Pureline (Lineal)

4

Logsig (Sigmoide)

### Funciones de transferencia: "hard"
![[Pasted image 20240604113501.png]]

### Funciones de transferencia: "soft"

![[Pasted image 20240604113515.png]]

![[Pasted image 20240604113528.png]]

La función Relu, de manera elegante, filtra solo los valores positivos.
La diferencia entre softplus y rectifier, por ejemplo, en Rectifier no hay una derivada, por lo que no podemos medir el cambio, en softplus si podemos, igual que en Leek

### El perceptron: Ejemplo
Considerando una neurona con hardlim como funcion con una entrada binaria (0 o 1), la neurona ya está entrenada.

**5**

**Las neuronas son consideradas operadores booleanas**
**El perceptron puede modelar cualquier puerta binaria simple.**

**6**

Con una sola neurona no es posible clasificar patrones complejos, como XOR o XNOR, dado que solo puede clasificar en líneas, para esto sería necesario una Red Neuronal.

![[Pasted image 20240604114639.png]]

En las capas ocultas es generalmente donde ocurre toda la magia, donde están las funciones importantes. 
Para las redes convolucionales o recurrentes, por ejemplo, suceden porque las capas ocultas tienen funciones adecuadas
La capa de salida si tiene neuronas. Es donde están las funciones que transmiten la salida.

![[Pasted image 20240604114948.png]]


### Cómo resolveríamos XNOR?
8

Sigmoidal
![[Pasted image 20240604115757.png]]

En este ejemplo, se tiene una capa oculta con dos neuronas, y una capa de salida con una neurona.
El secreto para implementar una red es poder manipular los subindices para peinar toda la red, de arriba a abajo, de capa en capa.

### Estructuras profundas

La profundidad de una red neuronal se mide usando la ruta más larga

### MLP como función Boolean

- MLPs como funciones "Boolean universales"
	- Puedo calcular cualquier función con cualquier numero de entradas y/o salidas
- Pero cuantas capas necesito?
### Composición de bordes completos.
![[Pasted image 20240604121541.png]]En este caso, para clasificar entre lo que va dentro y fuera, necesito 5 neuronas, una por cada linea.
Y necesito 3 capas en total, una de entrada, una oculta, y una que haga la intersección entre las 5 lineas. Es decir, un total de 6 neuronas

![[Pasted image 20240604121649.png]]

 Así aumentando la cantidad de neuronas, de más en más, en más, puedo hacer formas más complicadas, al punto que puedo reconocer la forma de un humano o un animal.

### Aprendizaje
- Las RN son funciones universales de aproximacion
- Pueden modelar cualquier funcion booleana
- Pueden modelar cualquier borde de clasificacion
- Pueden modelasr cualquier funcion de valores continuos
#### Pesos
![[Pasted image 20240604121948.png]]
El peso es la sinapsis, representa la intensidad de una conexión, y con cada ejemplo este se ajusta.
**Nota:** Si una capa es densa, significa que todas las neuronas se conectan con todas las otras neuronas.

MLP: MULTI LAYER PERCEPTRON

La general es FMLP, pero existen varias formas distintas, [[Graph Neural Networks]], [[Transformers]]... entre otras

### Cómo resuelvo las dimensiones de la matriz? 

A priori, la ecuación es: $$W^{\left(k\right)}=L_{k=1}x\left(L_{k}+1\right)$$
![[Pasted image 20240604122915.png]]

El bias de cada neurona también tiene su propio peso.
Cada neurona que no está en la capa de entrada tiene un bias asociado, y al igual que el peso, tiene un valor que sorprende.
