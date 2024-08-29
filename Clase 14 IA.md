## Redes CNN: Arquitecturas
### VGG
Tiene bloques y patrones de diseño, una de las más impresionantes

### Residual Network

Tiene un modelo en que la información de salida de una capa, se salta dos capas, y se une con la salida de la capa que sale después del salto, de esa manera no se pierden ciertos datos de la entrada.

### U-Net
Despues de downsampling, se hace una operacion de upsampling## LENet

### LeNet


## Redes neuronales Recurrentes

Se diferencian de las redes anteriores en los patrones que analizan. Especificamente estos, analizan algo con una secuencia, puede ser una señal, o un sonido, una frase, etc.
Si entendemos un patron, podemos usarlas para predecir un valor futuro. 
Analizamos patrones a lo largo del tiempo, por lo tanto estas redes funcionan a lo largo del tiempo.
Se caracterizan por agregar retroalimentación, no solo son feedforward. Esto se conoce como la "memoria", o "historia"
Esto es lo que permite analizar una secuencia, que es lo que permite hallar el patron.
A diferencia de las CNN, la retroalimentación ocurre en la capa oculta. Es aquí donde sucede todo. Vale recalcar que igual, al ser una red, tiene capa de entrada, oculta, y de salida.
Los patrones están no solo en los datos de las señales, pero tambien en la secuencia de estas señales.

### Como funcionan?

La capa oculta se replica una y otra vez, copiada por cada segmento elemento de la secuencia. 
Se ingresa **un vector**, y para el primer elemento, pasa por la primera copia de la capa oculta, lo que da una salida, en la forma de un vector de salida, que es el resultado de hacer la operación.

Al introducir el segundo elemento, el elemento será concatenado con la salida del primero, y ambos elementos ingresan directamente a la segunda copia de la capa oculta, y la salida de eso se concatena con el tercer elemento para entrar a la tercera copia, etc.

La razon por la que en los graficos se ve como una sola capa oculta que se reitera, en realidad es la misma capa repetida muchas veces una tras la otra, y se lo ejecuta con la entrada nueva mas la salida anterior.

Cada copia llamaremos "Time-step", 

Por cada time-step podremos predecir el cuarto, o el comportamiento del cuarto. Dado que tenemos una salida por cada time-step. Esto se llama "estado de secuencia"

Vale mencionar que si bien se visualiza con una adimensión, horizontal, dado que cada time-step lleva en si una capa oculta, a la que se le da una salida, es esencialmente una red, por lo que hay una segunda dimension vertical, de calculo en cada time-step

### Delay

Dado que se da de inicio como hiperparametro cuantos elementos quiero recordar, en caso de que quiera predecir algo a, por ejemplo, 3 time steps en el futuro, lo que se puede hacer es, predecir el siguiente timestep con los 5 time steps que tengo de entrada, luego, con el timestep predicho, uso del timestep 2 hasta el nuevo, y uso estos para predecir el 6, y asi hasta llegar al deseado.
Vale recalcar que dado que el timestep 5 lleva la informacion predicha usada con el timestep 1, la informacion del timestep 1 no se pierde.

### RNN con skip

Se puede hacer como en las redes con skip vistas antes, y pasar los datos en una red con dos capas recurrentes, y se pueden saltar las capas recurrentes para mantener los datos originales. Es decir, paso la entrada a la capa recurrente 1 y a la 2, para que estos datos se junten con la salida de la capa recurrente 1, etc. Esto es en parte la razon del exito de los Transformers

### Tipos de problemas que resuelve

Uno a uno, una entrada y una salida, como las MLP

Uno a muchos, es por ejemplo, para describir una imagen, se da una imagen, y se da una descripcion

Muchos a uno, si tengo por ejemplo, muchas palabras y quiero predecir la siguiente palabra

Muchos a muchos: por ejemplo si quiero predecir el precio del petroleo, si no es en paralelo, o o si es en paralelo, podria ser la traduccion de una oracion.