	## Introducción a las redes neuronales convolucionales - CNN

### Qué son?

- Las redes CNN son una categoria de redes neuronales que han demostrado ser muy eficaces en areas como vision artificial, el reconocimiento y clasificacion de patrones en imagenes
- Han tenido exito en la identificacion de rostros, objetos, etc
- La clasificacion de imagenes consiste en alimentar una imagen al algoritmo de clasificacion y generar una probabilidad de pertenencia a una clase, o las probabilidades de las clases que mejor describen la imagen.
- Para los humanos el reconocimiento de imagenes es una de las primeras habilidades que aprendemos desde el momento en que nacemos y se presenta de forma natural y sin esfuerzo como adultos.
- Sin esfuerzo podemos identificar de forma rapida y sin problemas el entorno en el que nos encontramos, asi como los objetos que nos rodean.
- La CNN no solo clasifica, si no que tambien te permite hacer la extraccion de informacion de una imagen. Esto lo hace porque si bien para nosotros la imagen es un objeto, para la cnn es una matriz de vectores.
- Vale recalcar que las CNN necesitan matrices de 3 dimensiones, no funcionan solo con dos, pero existen trucos. Por ejemplo, las imagenes en blanco y negro serán matrices en las que la tercera dimension es simplemente 1.
- Utilizamos Voxels, con volumen. No pixels que solo son 2D. Esto no es posible en una MLP.
- Son capaces de predecir semánticamente qué voxel pertenece a qué clase.
- Son capaces de reconocer intenciones porque son capaces de reconocer vectores de movimiento y desplazamiento.
### Inspiración
- Modelo Hubel y Wiesel.
	- Las CNN se desarrollaron inicialmente en la decada de 1980, inspirado por sus descubrimientos sobre la corteza visual de los gatos.
	- Descubrieron que cuando un mamifero veía un patrón, ciertas neuronas especificas se encendian, mientras más complejo el patron, más neuronas es encnedian.
	- Las Celulas S se activan, por ejemplo, cuando identifican formas basicas como lineas en un area y un angulo especifico
	- Las celulas C tienen campos receptivos mas grandes y su salida no es sensible a una posicion especifica en el entorno. Las celulas C responden a ciertos estimulos, aunque cambie su posicion absoluta en la retina.
	

### Neocognitron
- Kumihiko Fukushima en 1980
- Identifico deficiencias en el modelo hubel-wiesel
- Una de las prncipales: la invariancia de posicion de entrada ([[shift invariance]])
- 
- Celulas especificas se disparaban incluso si la imagen se movia a una ubicación diferente en su campo de visión. 
- Fukushima propuso el NeoCognitron.
- Esto es importante, porque sin importar donde se mueva el patrón, la red neuronal será capaz de reconocerlo.
- En una red 2D no se puede identificar si un objeto se mueve, porque no hay forma de identificar que los pixeles movidos pertenecen al mismo objeto. Pero al momento que es en 3D, agregamos voxels con volumen, se puede mantener la relacion de a qué pertenece esa porción, esto es [[Shift Invariance]]

![[Pasted image 20240618114905.png]]
![[Pasted image 20240618121357.png]]
Artquitectura tipo Sanduche SCSCSC
La primera capa de neuronas S es la capa de convolucion, la siguiente es downsampling.
Esencialmente, las células S detectan patrones específicos en en la capa anterior. (Que puede ser la capa C o la retina que proporciona la entrada.)
Las celulas tipo C especializan lo que halló la celula S. "Refinan" la respuesta de los planos correspondientes de las capas S.

Al hablar de CNNs hay dos etapas.
La primera etapa es conocida como etapa convolucional, esta extrae las caracteristicas del patron de interes en la imagen. ==La salida de esta etapa es un volumen.== 
La segunda etapa es la de clasificación, es decir, en la capa de "salida" de la red convolucional, se tiene un clasificador. Que puede ser, por ejemplo, un regresor logistico o una red MLP.
Dado que las MLP requieren un vector de entrada, se necesita un proceso que transforme el volumen en un vector. 

- Las redes CNN son muy similares a las redes neuronales: están formadas por neuronas que tienen pesos, bias, funciones de umbral y error, etc.
- Cada neurona recibe entradas, realiza el "producto punto" (convolution), de ahí su nombre, y utiliza una función de activación.
### Entonces, Qué cambia?
- LAs arquitecturas de las CNN suponen explícitamente que las entradas son imagenes de 3 dimensiones lo que nos permite codificar ciertas propiedades en la arquitectura
- No todas las neuronas se conectan con todas las siguientes neuronas, solo aquellas en el campo de vision (filtro, kernel). Son estos filtros o kernels, los que especializan el patron. Las capas S se encuentran mas cerca de la entrada, las que tienen los filtros o kernels que reconocen los patrones más simples. Mientras más te adentras a la red, los filtros son más especializados, mientras más te acercas a la salida, más profundo estás, tienes composición de estos patrones simples, y reconoces patrones más complejos. Esto quiere decir que cuando te acercas a la capa de salida tienes una composicion libre de ruido que se pasa al clasificador, solo con los patrones complejos identificados.
- Hay neuronas que se especializan en los patrones a desccubrir, recduciendo los parametros W que la red aprende.
- La razon por la que no todas las neuronas se conectan con todas, es que tienen un FOV, solo se encienden las neuronas relacionadas al patron en el FOV.

### Convolucion

Si tengo un aimagen de 5x5, tendremos un kernel, un filtro, un subcampo de visión, y extraemos el patron correspondiente, a travez de un patron de convolucion, una porción de 3x3, por ejemplo. Recordar que al ser una neurona, igual tiene Bias.
![[Pasted image 20240618120345.png]]

Se hace un barrido de la imagen con un "filtro" o kernel
	Notar que el filtro es un perceptron, con pesos y un bias.
![[Pasted image 20240618121329.png]]

Vale recalcar que se usa una doble sumatoria en la operación, porque el filtro va a barrer de arriba a abajo e izquierda a derecha la imagen.
![[0_faJQRB08AFT4C3Z5.gif]]
![[Pasted image 20240618121413.png]]


Pasamos el filtro por toda la imagen, y creamos un mapa de activación, que representa una abstracción de la imagen.
Si incremento el tamaño del filtro, el tamaño del mapa de activación se va a ver disminuido, dado que habrán menos operaciones, y por lo tanto menos resultados. Igual que si movemos la velocidad a la que se mueve, si hago que se mueva de 2 en 2 pixeles, por ejemplo (Esto se conoce como STRIDE, y es como  la velocidad de aplicacion del filtro.

Pero ahora las imagenes no son en 2D, tenemos imagenes en 3D, por lo que existirán 3 canales, lo que haremos es crear un filtro que mappee cada canal, luego, cada slot del resultado de cada canal, será sumado con el de los demás canales.

![[1_ciDgQEjViWLnCbmX-EeSrA.gif]]

El filtro se especializa de capa a capa.
- Hay tres tipos principales de capas:
	- Capa convolucional (No son capas simples, son volumenes de capas.)
	- Capa de pooling, y
	- Capa totalmente conectada (como en las RN)
![[Pasted image 20240618122439.png]]

Si tengo una imagen 32x32x3, debo crear un filtro 3d para la convolucion, por ejemplo, 5x5x3.
El resultado sera un numero de convolucion. **Los primeros filtros siempre deben tener la misma cantidad de canales que la entrada.**

Puedo establecer varios filtros, le primero me dará un mapa de 28x28x1, pero si aplico varios filtros, la profundida aumenta, entonces si aplico 6 filtros, tendré un mapa de 28x28x6, por lo que la siguiente capa convolucional deberá tener un filtro de **5x5x**6

![[Pasted image 20240618122753.png]]

La cosa de las CNN, es que la parte convolucional extrae las caracteristicas importantes de la imagen, y genera un mapa de estas caracteristicas sin ruido. Esto hace más sencilla la clasificación.