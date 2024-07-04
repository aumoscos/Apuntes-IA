## Regresión Logística
Es otro modelo simple en [[Machine Learning]], la diferencia es el tipo de problemas que resuelve.
Si quiere clasificar problemas de clasificación, cosas como identificar si una imagen tiene o no un tumor, identificar a quien le pertenece una cara, etc. Cosas que no se pueden resolver con solo predecir un número, como hace la [[Regresión lineal]].

Se requiere una función que establezca un límite de salida del modelo.
En la [[Regresión lineal]] predecíamos valores esencialmente infinitos. >0 o <0
Aquí, sin embargo, necesitamos un modelo lineal que clasifique y=0 o y=1
Una función lineal que pueda predecir valores 0<= hw (x)<=1
Una función que se comporta de esa forma es la función "Logistica"
### Representación de la hipótesis
$$g(z)=(1)/(1+e^-z)$$
Recordar: $h_w(x)=w^tX$

$z=w^tX$
![[Pasted image 20240530113058.png]]
$h_{w}\left(x\right)=\frac{1}{1+e^{-w^{T}x}}$


![[Drawing 2024-05-30 11.31.51.excalidraw]]
Función Sigmoidal
Función Logistica

Predice "y=0" si $h_w(x)<0.5$
$w^tx$<0
$g(w^tx)<0.5$; cuando $w^tx$<0
Predice "y=1" si $h_w(x)>=0.5$
$g(w^tx)$>=0.5; cuando $w^tx>=0$

$h_w(x)$ = probabilidad que y=1, para la entrada x

Por ejemplo: Si x=($x_0, x_1$) = ($1,Tamaño Tumor$)

Si, $h_w(x)=P(y=1|x;w)$;probabilidad que y=1, dado parametrizado x=0

### Bordes de decisión no lineales

Dependiendo de la función, se puede tener un borde de decisión que sea por ejemplo un circulo, o algo por el estilo, si agrego mucho el grado del polinomio, puede ser una forma extraña, incluso.
Pero a efectos prácticos acaba siendo lo mismo. 

Vale recalcar que esto devuelve una probabilidad a que el dato de entrada pertenezca a la clase 0 o 1, queda en mi decidir la clasificación final.

Vale también mencionar que la Regresión Logística clasifica una entrada. Alternativamente, si deseo tener varias variables, deberé tener varias neuronas.

### Regresión Logística

![[Pasted image 20240530115155.png]]
Igual nos manejamos con pares ordenados, porque seguimos en [[Aprendizaje supervisado]], por lo que debemos dar entrada y salida.


![[Pasted image 20240530115225.png]]

Siempre debemos empezar con $x_0$, dado que ese es el Bias.

### Función de costo.
Para poder determinar los w finales, necesitamos una función de costo o error. 
Esta será distinta a la de [[Regresión lineal]], dado que esa nos da un promedio de qué tan lejos estamos de un valor, sin embargo, esta clasifica entre 0 y 1, y distingirá si el valor fue clasificado correctamente

Costo = $-log(h_w(x))$ Si y=1
		$-log(1-h_w(x)$ Si y = 0
Costo$(h_w(x),y) =y(-log(h_w(x)) -(1-y)-log(1-h_w(x))$

### Gradiente descendiente.

$J\left(W\right)=-\frac{1}{m}\Sigma_{i=1}^{m}$$y^{\left(i\right)}\log h_{w}\left(x^{\left(i\right)}\right)+\left(1-y^{\left(i\right)}\right)\log\left(1-h_{w}\left(x^{\left(i\right)}\right)\right)$
![[Pasted image 20240530115921.png]]

![[Pasted image 20240530115942.png]]


![[Pasted image 20240530120251.png]]

### Clasificación multi-clase: Una vs. Todas

Clasificamos de manera que la salida puede estar dentro de varias clases.

Ej: Clasificar un email entre "Familia", "Amigos", "Spam", "Trabajo", etc.
En cuyo caso la salida sería y=1, y=2, y=3, y=4...

En este caso se hace "Una vs todas", lo que quiere decir que analizamos cada una de las clases vs cada una de las otras.
![[Pasted image 20240530120609.png]]

## [[Redes neuronales]]

### Qué son?
![[Pasted image 20240530121052.png]]

Todo empieza en su forma más básica, el cerebro como tal.
Vale la pena recalcar que no se está intentando emular o imitar las neuronas del cerebro real. Usamos abstracciones inspiradas para poder tener un proceso de decisiones similar.

Viendo una Neurona real, tienen varios elementos, de los cuales tomaremos cuatro elementos
![[Pasted image 20240530121346.png]]
- El Núcleo es donde sucede todo el procesamiento (La función)
- La Dendrita es el input (Vector X)
- El Axon es el output
- Las Sinapsis son las conexiones entre la salida y la entrada de otra neurona, estas miden la intensidad con la que uno se conecta al otro. (Los w)

El cerebro tiene $10^1.^1$ "elementos", cada una tiene en promedio $10^4$ conexiones.
Lo que decidimos usar en redes neuronales son el procesamiento, las entradas, salidas, y la sinapsis.

### Neurona artificial

![[Pasted image 20240530121953.png]]

Las entradas X se multiplican por sus respectivos w, se suman, se definen, y se pasan por la función de umbral que decide si se activan o no.

La neurona puede estar conectada a una red. Si la neurona es la entrada, los x serán los ejemplos, sin embargo, si no es de la entrada, y está conectada con neuronas anteriores, los x serán definidos por las salidas de las neuronas.

La función final puede ser una de muchas técnicas de IA, puede ser por ejemplo, regresión lineal, donde los x son una imagen, y se decide si estas son un u otro objeto.

Este modelo es conocido como el [[Perceptron]], se utiliza mucho, incluso en los transformers.

El perceptron fue introducido por McCulloth y Pitts en 1963

