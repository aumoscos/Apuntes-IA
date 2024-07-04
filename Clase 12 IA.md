## CNN Salida

Vale recalcar que la salida de la ultima capa oculta, la que alimenta la parte de clasificación, es un vector con los mejores W que encontré que produce la imagen. 

##  Ventajas de las CNN
- Shift Invariance
- El FOV, permite solo tener las neuronas necesarias activas, solo conecta neuronas especificas, no conecta todas contra todas. Esto reduce el número de Ws, ahorra espacio y memoria, y las hace más especificas. Conexiones dispersas en lugar de full connected. 
- Además se comparten los pesos en toda la imagen, lo que reduce los requisitos de memoria y la equivarianza traslacional. (Esto es porque el filtro tiene sus Ws, y cuando se mueve para peinar el resto de la imagen, los W no cambian.) 
	- Los W solo cambian cuando se ajusta el filtro, que esto solo sucede cuando ya acabé todas las convoluciones y he clasificado la salida, una vez que tengo eso, recién mido el error y se hacen los ajustes. Antes, en la parte de convolución aún no tengo una salida, debo esperar hasta que se haya hecho la clasificación para saber si ha cambiado.
	- Dado que comparten los pesos, con la misma comparación, no importa donde encuentre el patrón, lo encontrará igual, porque los pesos están compartidos. El patrón se traslada a la siguiente capa siempre, esto es la traslacional equivariance
- Las CNN utilizan un concepto muy importante de pooling o sub-muestreo (O downsampling), en el que los pixeles mas destacados se propagan a la siguiente capa eliminando el resto. Esta es la especialización que hace la capa C. No tiene neuronas, tiene operaciones.

## Translational Equivariance y Shif Invariance

- Equivarianza traslacional, se refeire a la capa de compartir pesos, eso produce un efecto en el reconocimiento de patrones o caracteristicas en una imagen independientemente de su posicion en el espacio.

## Stride

![[Pasted image 20240620114816.png]]
Es un hiperparametro que yo establezco, y va a modificar la salida. 

==Formula del Stride:==
Tamaño de la salida:
((N-F)/stride)+1
N: Tamaño de imagen original
F: Tamaño del filtro
Para que el stride sea valido, debe ser entero.

Por ejemplo:
N=7, F=3
stride 1 => (7-3)/1 + 1 =5
stride 2 => (7-3)/2+1 = 3
stride 3 =>(7-3)/3 + 1 =2.33

En este caso, con un tamaño de imagen de 7x7, y un filtro de 3x3, un stride de 1 y 2 seria valido, pero un stride de 3 no.

Vale recalcar que la entrada siempre debe ser cuadrada, y en caso de no serlo, la debo transformar a una cuadrada.

- Debido a que el tamaño del mapa de caracteristicas siempre es mas pequeño que la entrada, para evitar que el mapa se reduzca, usamos Padding (o relleno)
- El padding consiste en agregar una capa de pixeles de valor cero alrededor de la imagen, así el mapa de características no se ve afectado.
- Además de mantener el tamaño, después de realizar la convolución, el padding también mejora el rendimiento y asegura que el tamaño del kernel y el stride encajen con la imagen

Una técnica es agregar padding en todos los bordes de la imagen, dado que al momento del barrido, los datos en las esquinas se verán menos que los que están en el centro, por lo que si agregamos filas y columnas de padding, las que se verán menos por estar en las esquinas serán las de cero, que son irrelevantes. (Esto también se usa en lenguaje natural, dado que no se puede controlar el tamaño exacto del texto recibido.)

En el ejemplo anterior: 
N=7, F=3, con stride = 3
Se puede agregar padding de 1 pixel en el borde para hacer que el stride de 3 funcione

(9-3)/3 + 1 =2

En otro ejemplo

Imagen de entrada: 32x32x3
10 filtros 5x5 con stride 1, pad 2
cual es el tamaño del mapa de salida?
((32+2x2)-5)/1+1 = 32

Y cual es el numero de parametros?
Cada filtro tiene 5x5x3 + 1 (el bias), que es 76 parametros
Por 10 filtros, esto es 760 parametros.

EJERCICIO PIDELE A ALGUIEN QUE LO HAYA COPIADO
60 = ((N+2P-F)/S) +1
60 = ((60+2P-3)/1)+1
59=60+2P-3
2=2P
P=1


## Extracción de características

- Luego de la capa de convolución, tenemos la capa de pooling:
	- Una vez concluida la convolución; esto es, una vez obtenidos los mapas de características, es común agregar una capa de pooling o submuestreo.
	- La capa de pooling tiene el propósito de reducir el tamaño espacial de convolución.
	

==**Nota:** Recuerda que la regresión lineal se usa para estimar un valor, basado en la relación entre la entrada y salida==
 
### Tipos de pooling

#### Max pooling

Se basa en filtrar el valor máximo de la sección de la imagen cubierta por un filtro.
Max Pooling tambien funciona como un supresor de ruido
Descarta la activaciób ruidosa junto ocn la reudcción de dimensionalidad.
==LA CAPA DE POOLING NO TIENE NEURONAS, SOLO HACE FUNCIONES==
![[Pasted image 20240620121406.png]]

#### Pooling promedio

Filtra el promedio de todos los valores de la parte de la imagen cubierta por el Kernel.
Tambien realiza la reducción de dimensionalidad como un mecanismo de supresión de ruido.

![[Pasted image 20240620121419.png]]


## Extracción de características.

En las capas de pooling no hay funciones de activacion, ni neuronas. La cantidad de funciones y capas será igual a la cantidad de capas en la parte de convolución.

Los parametros de las capas convolucionales y la capa MLP se "aprenden"
Las capas de reducción (pooling) son fijas y no se aprenden

- La capa convolucional + funcion de activacion y la capa de pooling forman juntas una capa ith o volumen de una red neuronal convolucional

- Despues de la convolucion y las capas de pooling, la etapa de clasificacion consta de pocas capas conectadas
- Estas capas totalmente conectadas solo pueden aceptar datos de 1D
- Hay que convertir los datos 3D de la parte convolucional a 1D
- El numero de parametros a aprender: en la primera capa convolucional
	- La primera capa convolucional contiene $K_1$ filtros, cada uno de tamaño LxLx3
	- Esto es, en total $K_1\left(3L_{j^{}}^2+1\right)$ parametros 
		- +1 porque cada filtro tambien tiene el bias
- Imagen de entrada: 32x32x3
- 10 filtros 5x5 con stride, pad 2
- parametros de esta capa = 10*(3(25)+1) = 760



