**Nota:** Si después de varias iteraciones del [[Gradiente descendiente]], el error sigue disminuyendo pero muy lentamente, aparte de aumentar el $\alpha$, podemos reiniciar el proceso con valores W diferentes.

## Aprendizaje: Corrección del error - Back-propagation
- Recordar que tenemos redes de neuronas... no una neurona
- El back propagation significa ver el error total, es decir, ver cuanto contribuye cada neurona al error.

## Aprendizaje: Red MLP derivable
$y=\alpha\left(W_{1,1}^3y_1^2+W_{2,1}^3y_2^2\right)$
![[Pasted image 20240611114257.png]]

## Aprendizaje: El problema
![[Pasted image 20240611114329.png]]

**Nota:** Características de las MLP: Todas las neuronas están conectadas de todas las neuronas, es feed forward, y la entrada siempre siempre siempre es un vector. Así sea una imagen en 2 dimensiones, esta debe ser convertida en un vector. La razón por la que necesitan un vector, es porque la hipótesis de una MLP es W transpuesta por X

## Aprendizaje: Gradiente descendiente
![[Pasted image 20240611114853.png]]

- Solución Iterativa
	- Empezar en un punto inicial (aleatorio)
	- Encontrar el punto en que cambia la dirección, para disminuir el error
		- Esto es, encontrar la derivada de la de la función:
		- Una derivada positiva, moverse a la derecha aumenta el error
		- Una derivada negativa, moverse a la derecha disminuye el error

El gradiente descendiente se detiene cuando la derivada llega a 0, este es el mínimo local o global.

- Hay varios tipos de cálculo del Gradiente Descendiente, que difieren en la forma en la que manejan lso conjuntos de datos:
	1. Batch Gradient Descent (Batch)
	2. Stochastic Gradient Descent (Online)
	3. Mini-Batch Gradient Descent (Mini-batch)
	Cual se usa es decisión propia.

## Aprendizaje: Regresando al problema
![[Pasted image 20240611114329.png]]

Qué son los pares de entrada y salida, qué es f() y cuales son sus parámetros? Qué es la divergencia div?

## Aprendizaje: Notación Vectorial
Dado un conjunto de pares entrada-salida, para entrenamiento
![[Pasted image 20240611115441.png]]
![[Pasted image 20240611115535.png]]

### Tensores
- Escalar: Tensor de dimension 0  (0D) Por lo tanto, tiene 0 ejes y es de rango 0
- Vector: Tensor de una sola dimension (1D). Un Vector tiene 1 eje y es de rango 1
- Matriz: Tensor de rango 2, o 2 ejes, organizada en filas y columnas, tecnicamente es un Tensor de 2 dimensiones (2D)
- Tensor 3D (y mayor dimensionalidad): Si bien, técnicamente todas las estructuras anteriores son tensores válidos, los tensores generalmente se refieren a las matrices de 3 o más dimensiones.
Esencialmente, los tensores son matrices de matrices. la dimensionalidad de estos no tiene limite.
Se ha recalcado antes, pero estas operaciones de matrices por matrices por matrices tomarían demasiado tiempo y poder computacionalidad. Es gracias a numpy que es posible realizar estos cálculos rápidamente.

![[Pasted image 20240611115543.png]]
Se puede usar 1 o dos neuronas como salida tambien, una encendida significa la salida deseada y la otra no.

Salida multiclase representacion one-hot
- Considere una red que debe distinguir si una entrada es: perro, mono, flor, sombrero o gato.
- Podemos representar este conjunto con el vector: 
- [perro, mono, flor, sombrero, gato]
- Para entradas de cada una de estas clases la salida es:
- perro = [1 0 0 0 0 ]T
- mono = [0 1 0 0 0 ]T
- flor = [0 0 1 0 0 ]T
- sombrero = [0 0 0 1  0 ]T
- gato = [0 0 0 0 1 ]T
- Para una entrada de cualquier clase, tendremos un vector de salida de cinco dimensiones, con cuatro ceros y un 1 en la posición de la clase correspondiente.
- Esto se conoce como one-hot encoding.

Es común utilizar la función de activación Softmax en la salida de las redes de clasificacion multiclase
$z_{i}=\Sigma_{j}W_{ji}^{n}y_{j}^{n-1}$
Por ejemplo: tenemos imágenes de digitos junto con la etiqueta del digito representa la imagen
- Resolver:
	- Reconocimiento binario: Esto es un "2" o no?
	- Reconocimiento multi-clase: Qué digito es? Este es un dígito?
	- En este ejemplo, las imagenes que corresponden a un 2 son 1, el resto son 0
	- Pero tambien podemos tener uno que reconozca cada numero, necesitamos 10 salidas, en cuyo caso la estructura será la misma, pero con 10 neuronas en la capa de salida.

![[Pasted image 20240611115555.png]]

Vale recalcar que, como Relu tiene un pico, y ese pico no es derivable, existen otras funciones similares que no tienen ese pico, como ReLu exponencial, Leaky ReLu, ReLu paramétrico.

## Aprendizaje: Ejemplos de funciones div()
![[Pasted image 20240611122014.png]]

![[Pasted image 20240611122049.png]]

![[Pasted image 20240611122139.png]]

## Aprendizaje: Recordar notación

- La capa de entrada es la capa 0^th
	- Entrada a la red: $y^{\left(0\right)}=x_{i}$ (Si el superíndice k es 0, significa la entrada) 
- La salida del perceptron $i^{th}$ de la capa $k^{th}$ es $y_{i}^{\left(k\right)}$
- El peso de la conexión entre la unidad

**Nota:** Cada capa de perceptrones se puede considerar como un vector de activación.
a

