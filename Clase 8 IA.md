## Redes Neuronales
### Pesos
![[Pasted image 20240606110651.png]]
**Recuerda:** La función se ajusta con los parámetros $w$
$h_{w}\left(x\right)=w^{T}x$ (W y X son vectores con sus propias dimensiones)
$h_{w}\left(x\right)=w0+w_1x_1+w_2x_2+\cdots+w_{n}x_{n}$
Mientras mayor es el parámetro w, la red neuronal le presta mayor atención a las neuronas con estos valores altos, dado que estos valores altos producen el mayor error.

- Mientras mayor es el número de términos polinómicos, más ajustada es tu red, esto significa mayor accuracy, pero también overfitting.
- Lo mismo sucede en RNs, mientras más neuronas tenemos, más ajuste vamos a tener, en este caso las neuronas funcionan como características, si se tiene una red demasiado complicadas, el primer paso tiende a ser eliminar neuronas.

- El "bias" de cada neurona también contiene un peso.
- Vale recalcar que solo las neuronas tienen bias, las entradas no.
- El w0, al igual que el resto de parámetros, se descubre mientras que se entrena el modelo.
![[Pasted image 20240606111548.png]]
### Aprendizajes
![[Pasted image 20240611110855.png]]

Para el aprendizaje supervisado necesito pares de datos, la entrada, y el valor esperado.
En caso de imagenes, por ejemplo, se ingresa la imagen y el [[Ground Truth]], que es la verdad, el valor esperado, puede ser una etiqueta, o la máscara de un tumor, etc.

Esto se alimenta al algoritmo (En este caso una red neuronal)

Y esto generará una hipótesis, una función. Que realmente es una matriz de números que reflejan todo lo que la red neuronal tiene, sus parámetros y valores.

Vale la pena recalcar que ninguna red te va a dar el label como resultado. Te dará un numero de probabilidad.

### Entrenamiento
Buscamos una estrategia iterativa que permita a la neurona adapte sus parametros de conexion, cuando se presentan los datos de entrenamiento la entrada de la red.


Dado que hay muchas neuronas conectadas, cambiará un poco.
Lo único que cambia es la variacion del W
W nuevo = W anterior - $\alpha\Delta J$
$\alpha\Delta J=\Delta W$

$\Delta W_{ij}=\alpha\left(T_{j}-Y_{j}\right)Y_{i}$
![[Pasted image 20240611111441.png]]

#### Aprendizaje

- Seleccionar $\alpha$
- Inicializar los pesos con valores aleatorios (W)
- Mientras todos los ejemplos no sean clasificados correctamente
	- Ingresar un nuevo ejemplo a la red
	- Si el ejemplo fue incorrectamente clasificado
		- W nuevo = W anterior + $\alpha\left(t-y\right)x$

**Nota:** Se pueden hacer regresores lineales y logisticos utilizando redes neuronales, es más, solo deberia necesitarse una neurona para esto.

##### Ejemplo

Entrenar un perceptron par que reconozca el patron de comportamiento de la puerta AND
Supongamos los siguientes parametros
$\alpha=0.3$
$\theta=1.5$
$W_1=0$
$W_2=0.25$
![[Drawing 2024-06-06 11.40.25.excalidraw]]

### Propagación hacia adelante - Forward propagation

Considere la siguiente red de 3 capas y 4 unidades de activación sigmoidal (neuronas con una función de umbral tipo sigmoidal)

Entrenar la red para reconocer los patrones de entrenamiento de la siguiente tabla

**DIEZ O VEINTE EPOCAS NO ES SUFICIENTE. Y NO HAY EXCUSA, NECESITAMOS USAR CEDIA O ALGO POR EL ESTILO EN EL PROYECTO. NO VA A ACEPTAR MENOS DE UN PAR DE CENTENAS**

