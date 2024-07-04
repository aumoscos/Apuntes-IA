## Aprendizaje en las redes CNN

---
> Side note: Recordar especificar en la tarea 3 solo el problema. No mencionar ni de chiste algoritmos de IA
> Por ejemplo, si se va a clasificar imagenes de diagnostico de clase, el problema seria:
> Clasificar imagenes relacionadas a diagnosticos de cancer.
> Debo solo ir por la parte de ingenieria.
> No vamos a hacer el diagnostico, pero si vamos a cargar y clasificar las imagenes.
> Debo considerar todos los casos de uso y los escenarios de estos. Por ejemplo, si alguien me sube una imagen de un perro, qué debo hacer? Si alguien me sube algo correcto, qué debo hacer? etc.
> Todo esto **Sin mencionar los algoritmos que usaré.**
> **NUNCA PONER COMO ACTOR EN EL SISTEMA  AL MISMO SISTEMA NI AL DESARROLLADOR**
> Tampoco se aceptarán cajas negras.
--- 
### Extracción de características.
![[Pasted image 20240625114158.png]]

En las CNN necesitamos 3 dimensiones. 
Esto pasa a las capas de convolucionales, con los filtros y neuronas. 
En una misma capa todos los filtros deben tener la misma dimesión. 
Se pueden tener la cantidad de filtros de salida que uno quiera, pero en la entrada.

![[Pasted image 20240625114726.png]]

### Redes neuronales convolucionales
Hiperparametros que debemos escoger:
- Numero de capas convolucionales y de pooling
	- El orden para ubicarlos. No necesariamente es SCSCSCSCS, que es el formato del neocognitron. En las CNN, tenemos volumenes, bloques de capas. Podemos tener una capa de convolucional alimentando a otra capa convolucional con filtros distintos, y recien entonces poner una capa pooling. Como yo quiera. Pero en general, el patron es convoluciones, seguidas de pooling, seguidos de mas convolucion. 
- Para cada capa de convolucion:
	- Numero de filtros $K_1$
	- Tamaño del filtro L1 x L1
	- La "profundidad" del filtro se fija por el numero de filtros en la capa anterior $K_{i-1}$
- El stride $S_{i}$ vale mencionar que esto tendra un efecto en la salida
- Para cada capa de reduccion o pooling:
	- Tamaño espacial del filtro P1 x P1.
	- El stride D1.
	- El tipo de pooling.
- Para el MLP final:
	- El numero de capas y numero de neuronas en cada capa.

En resumen, en las capas convolucionales
- La capa de convolucion espera imagenes de tamaño W1xH1xD1
- Requiere 4 hiper parametros
	- Numero de filtros K
	- Tamaño del filtro: F
	- Stride: S
	- Cantidad de cero padding:
- Produce una salida de tamaño W2xH2xD2

### Aprendizaje en CNN:

El entrenamiento de una CNN es similar al de las redes neuronales, utilizando Backpropagation y gradiente descendiente.

Aprendizaje en las CNN:
- En total los parametros que la red debe aprender:
	- En la última capa (MLP), todos los pesos y bias de cada uno de los perceptrones
	- En las capas convolucionales todos lso filtros
- Cada capa j tiene $K_{j}$ mapas.
	- $K_0$ es el numero de mapas en la entrada (3 canales de colores)

Con respecto a los parametros en el resto de las capas:
- Si $L_{j}xL_{j}$ es el tamaño de los filtros en la capa $J^{\th}$
- Para cada capa Jth se requieren Kj($K_{j-1}L_{j}^2$+1)
- Si se tiene una entrada de 32x32x3

### Back propagation
Como antes: para todas las i,j,k actualizar:
![[Pasted image 20240625121448.png]]