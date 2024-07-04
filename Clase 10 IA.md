## Aprendizaje: Entrenamiento con GD

### Aprendizaje: Regla "chain"

Pequeñas perturbaciones en x causan pequeñas en cada función
Para poder corregir el error que saco de la salida, necesito saber qué neurona causó el error de manera retroactiva. Esto es hace con las derivadas parciales.
![[Pasted image 20240613112845.png]]
Cada elipse representa un perceptron.
El propósito es calcular la derivada de Div(Y,d) c.r.a cada peso $w_{ij}^{\left(k\right)}$ y salida $y_{i}$

Vale recalcar que los superíndices indican la complejidad, mientras más alto el k, mayor complejidad y profundidad.
Los subindices se repiten, ya que iteran por cada capa. De manera práctica, se necesitarían dos lazos for, uno que recorra capa por capa, y uno que recorra las neuronas dentro de cada capa.
Se necesitaría también una función recursiva, que pueda hacer $W^{T}X$, sin importar donde esté.

La función Div la elijo yo, es fuera de la arquitectura, se usa para decidir qué tan cerca o lejos estamos del valor deseado.

### Aprendizaje: Forward

![[Pasted image 20240613113851.png]]

En la capa 1, $z_{j}^{\left(1\right)}=\sum_{i}^{{}}w_{ij}^{\left(1\right)}x_{i}$
en las siguientes, $z_{j}^{\left(k\right)}=\Sigma_{i}w_{ij}^{k}y_{j}^{\left(k-1\right)}$
![[Pasted image 20240613114241.png]]
### Aprendizaje: Backward

Una vez hecha la forward propagation, paso la salida por la función de divergencia, para que mida por cada una de las neuronas que tengo, mida cual es el error.

![[Pasted image 20240613114651.png]]

Una vez tengo el nuevo error, debo propagar el error, ese valor numérico (Será un vector con números) de regreso hasta los primeros W. 
La salida es un vector porque la entrada es un vector, la operacion que se realiza es una multiplicacion de vectores con vectores, y si la salida final es una sola neurona, se multiplica por un escalar. Cualquier vector multiplicado por otro vector o un escalar será un vector
Iré paso a paso, por la conexión entre cada una de las capas (W), y una vez que eso ha llegado hasta la primera capa, recién puedo decir que he propagado el error.

### Aprendizaje: Perceptron con activación derivable.

Estas derivadas nos dicen cuan sensible es una función con respecto a las variables que la definen.

Empezamos haciendo la inicialización del gradiente.
$\frac{\delta\text{Div}\left(Y,d\right)}{dy_{i}}=\frac{\delta\text{Div}\left(Y,d\right)}{dy_{i}^{\left(N\right)}}$
Derivada de y con respecto a z es igual a la derivada de w con respecto a x.
Es por eso que $\frac{\delta z_{j^{}}^{\left(N\right)}}{\delta y_{i}}=w_{ij}$
Vale recalcar que la razón por la que hay una sumatoria, es porque la neurona tiene varias conexiones, y tiene que afectar a todos. 

### Aprendizaje: Entrenamiento con BP
![[Pasted image 20240613120438.png]]

==**Leccion:** NO INICIALIZAR LOS W EN 0, SOLO EL ERROR, ES DECIR, LA DERIVADA DE LA FUNCION DE ERROR CON RESPECTO A W, SI INICIALIZO LOS W EN 0 NO VA A APRENDER NADA.==


![[Pasted image 20240613121131.png]]

![[Pasted image 20240613121208.png]]

Esencialmente, si quiero saber cuanto cambia el valor $y$ respecto a una entrada $z$, se halla el jacobiano, y este encuentra el valor, y nos dice cual es la derivada que tenemos que ingresar.
- El jacobiano contiene las derivadas de las funciones de activación de las neuronas c.r.a sus entradas
- Para salidas vectoriales: El número de salidas puede ser diferente al número de entradas en la capa de salida.
	- El jacobiano es una matriz con las derivadas parciales individuales de las salidas c.r.a las encuentra.
