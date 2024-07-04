## Algoritmos lineales: Gradiente Descendiente

wj = wj - a(delta/deltaw1)J(w1)
a = velocidad de aprendizaje

Si a es muy pequeño, el GD es lento
![[Drawing 2024-05-28 11.19.28.excalidraw]]

Si a es muy grande, GD puede exceder el mínimo, fallar la convergencia, o divergir. (Overshooting)
![[Drawing 2024-05-28 11.21.15.excalidraw]]
El alpha puede ser dinámico, puede cambiar mientras se va haciendo la búsqueda, por ejemplo, se inicia con un alpha grande, y mientras se va acercando a la parte más baja, va disminuyendo.

- Regresión lineal de una variable
	Jw(x) = w0 + w1x
	J(w0,w1) = 1/2m Sum(m,i=1)(hw(x^(i)-y(i))^2)

## Aprendizaje Supervisado - Un algoritmo básico de aprendizaje: regresión lineal

1. Regresión lineal simple o de una variable (n=1): Por ejemplo, determinar la temperatura en una zona, basado en las temperaturas históricas de esa zona.
2. Regresión lineal múltiple o de varias variables (n>1): Por ejemplo, determinar la temperatura en esa zona, que depende de varias variables o features, como: La presión atmosférica, viento, ubicación, otras.
3. Regresión polinómica: Es el caso más general de regresión lineal. Asume dependencia polinómica entre las entradas y la salida.

Se utiliza regresión cuando quiero:
- Encontrar una relación entre variables de entrada y de salida
- Cuando quiero calcular un valor.

## Aprendizaje Supervisado: LR - Múltiples variables
![[Pasted image 20240528113944.png]]
Donde:
m = número de ejemplos
n = número de variables (features)
$X^i$ = variables de entrada del $i^{th}$ ejemplo ejemplo de entrenamiento
![[Pasted image 20240528114114.png]]
![[Pasted image 20240528114140.png]]
![[Pasted image 20240528114200.png]]
Siempre usamos un vector W y lo multiplicamos por X para aprender.

Hipótesis= Con múltiples variables: ![[Pasted image 20240528114411.png]]

Por ejemplo: Precio de departamento = 80 + 0.1x1 + 0.01x2 +3x3 -2x4
80 es w0, y el precio base siempre será este, pero sin embargo, el valor final puede ser menor, dado que puede haber una penalización por edad, en este caso el negativo.

Algoritmo de gradiente descendiente
![[Pasted image 20240528114724.png]]

### Definición de la función de costo (pérdida, error o divergencia)
- El método es iterativo, a medida que determinamos el error de cada ejemplo, actualizamos los parámetros $w$ que definen el modelo
- Cómo sabemos si está funcionando bien?
- Comparamos el valor $h_w(x)$  "predicho" y el label (salida esperada) $y$ 

Minimizamos la función de error
- Buscamos que la diferencia entre $h_w(x)$ y $y$ sea pequeña, entonces el algoritmo hace un esfuerzo por minimizarla.

El borde de decisión de regresión polinómica cambiará si agregamos mayores grados de la función, por ejemplo, si tenemos una linea recta, puede no ser adecuado para los datos que tenemos, pero agregarle un $x^2$ nos dará una mejor predicción. En este caso la linea recta sería [[underfitting]].
![[Pasted image 20240528115521.png]]
Sin embargo, si agregamos mucho los grados, tendremos una función que sigue exactamente los ejemplos, y esto dará [[overfitting]] y no podrá reaccionar bien a datos nuevos que no siguen la función exacta.
![[Pasted image 20240528115629.png]]
Hay muchas razones para overfitting, pueden ser muy pocos ejemplos, features muy complejas, relación muy exacta, etc.

En este caso grado 2 o 3 podría funcionar, se busca un balance, dependiendo del % de error que vayamos a aceptar, ya que sabemos que 100% de accuracy generalmente es prueba de overfitting.

![[Pasted image 20240528115944.png]]

### Cómo resolver overfitting
- Opciones:
	- **==Incrementar el número de ejemplos**==
	- Reducir el número de características (n muy alto)
	- Podemos seleccionar manualmente las características que deseamos conservar o a través de reducción de dimensiones como PCA
	- Añadir un término de regularización (L1, L2) a la función de costo.
		- Mantener todas las características, pero reducir la magnitud/valores de los parámetros $w_j$
		- Funciona bien cuando tenemos muchas características y cada una contribuye poco a la predicción
L1
![[Pasted image 20240528120403.png]]
L2
![[Pasted image 20240528120417.png]]

Lambda debe ser el tamaño correcto, lambda muy alto causa underfitting, lambda muy bajo causa overfitting.

**PON ESTO DONDE SEA ADECUADO, PERO W0 ES EL BIAS**

Forward pass (O forward propagation) es calcular la salida con la entrada que se tiene.
Una vez calculada esa salida, se calcula el error. 
Con el valor del error, se lo ajusta a cada w utilizando el back propagation.
Esto quiere decir, que el error que tenemos en la salida, lo regresamos a los w que provocaron el error. Y debemos ajustarlos dependiendo del error.
Defendido el delta de cada w, lo cambiamos con la regla de aprendizaje.
Una vez hecho esto, con los w ajustados, el entrenamiento se ha hecho.

Todos estos algoritmos de IA son algoritmos de búsqueda, dado que esto es un algoritmo de búsqueda.

El inicio siempre será aleatoria, pero se pueden tomar varias formas de controlar la aleatoriedad de los valores iniciales, puede ser completamente random, distribución uniforme, dist. normal, etc. O incluso podemos usar [[transfer learning]]  para no iniciar de zero

Empezamos ingresando el primer ejemplo, hacemos los pasos mencionados antes, y luego hacemos lo mismo con cada uno de los siguientes ejemplos, ajustando los w con cada ejemplo.

O si no, podemos utilizar todos los ejemplos, introducimos cada ejemplo para el forward feed, y guardamos el error de cada uno, sacamos el promedio de todos los errores, y con ese número hacemos el aprendizaje. Esto se llama [[batch learning]]

También podemos hacer [[mini batch learning]], donde en lugar de usar todos los promedios, usamos subsets a la vez.
Si el mini batch es igual a 1 es online
Si el mini batch es diferente de 1 y de m, es mini batch
Y si es igual a m, es batch learning.

Nunca es suficiente usar un batch una sola vez, probablemente necesitemos mostrarle el mismo conjunto cientos de veces para que extraiga lo más que puede, esto es conocido como [[épocas]]

Se ajustará un poco y poco con cada época, que es la razón por la que se lo mostramos cientos y cientos de veces para que aprenda, y quede una función correctamente ajustada.