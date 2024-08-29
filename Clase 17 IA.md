
## LSTM Long Short Term Memory Networks
![[Pasted image 20240716112400.png]]

- Diseñadas explícitamente para evitar el problema del desvanecimiento a largo alcance
- Y recordar información durante largos periodos de tiempo
- Las RNN tienen la forma de una cadena de módulos repetitivos de una RN; este módulo tiene una estructura simple, por ejemplo una sola capa con una función de activación tipo tanh.

En estas, el estado de la capa oculta anterior pasa al siguiente paso de la secuencia
El estado anterior actúa como la memoria de las redes neuronales.

- Cuando tenemos un valor que se multiplica repetitivamente, puede "explotar", es por esto que cuando se hace forward propagation ,  a veces se da la explosion del gradiante, esencialmente el contrario del desvanecimiento.
- Para esto se usa la funcion tanh, que mantiene los valores entre -1 y 1, así no dejando que se vaya de largo el gradiente.
==**Nota: el contexto es un parametro que mide la cantidad de timesteps**

![[Pasted image 20240716114036.png]]
Fueron diseñadas explícitamente para recordar información durante largos periodos de tiempo.
Llaman la capa oculta "celdas", en donde tienen "gates", que son operaciones que se encargan de decidir qué valores se recuerdan.
Tienen redes neuronales simples, con funciones de umbral como la tangencial hiperbolica y la regresión logística.

![[Pasted image 20240716114435.png]]
La layer es una capa de RN
Componentwise es una operación Pointwise
También hay vectores, no mostrados, pero flechas solas. 
Concatenar es como se hace en las RNN, donde se agrega cierto valor.
Copiar, es pasar el resultado a más de un lugar.

![[Pasted image 20240716114838.png]]
La puerta del olvido decide qué informacion se pierde
La puerta de entrada decide qué info se pasa adelante
La salida hace la operación correspondiente.

![[Pasted image 20240716114852.png]]
- En las redes LSTM el estado de la celda es la línea horizontal que recorre la parte superior del diagrama
- El estado de la celda recorre toda la cadena de celdas
![[Pasted image 20240716115111.png]]

La mezcla de un vector con una operación elementwise es una puerta
La primera es la puerta del olvido, una sigmoidal con un elementwise
La segunda es la puerta de entrada, tiene 2 componentes, una sigmoidal con un elementwise, pero tiene una tanh también que reescala la operación, y llega a otra pointwise.
La tercera es la puerta de salida, esta toma lo que trajo el pasado, las decisiones pasadas de dejar pasar lo que corresponde.

![[Pasted image 20240716115340.png]]

Vale recalcar que en la ultima, no hay una red neuronal, solo es la función tangencial hiperbolica.
- El primer paso en la red es decidi que informacion va a eliminar del estado de la celda.
- Esta la toma la capa sigmoidal lalmada "puerta de olvido", y elimina objetos basado en que tan cerca está en cero, la sigmoidal se multiplica con lo que estaba en el pasado, y si lo decide, se olvida.
- ![[Pasted image 20240716115534.png]]
- ![[Pasted image 20240716115610.png]]
- ![[Pasted image 20240716115721.png]]
- Lo que sale de este, es la memoria actualizada, y es lo que se pasa por arriba, para la siguiente celda, pero no es la salida.
- ![[Pasted image 20240716115920.png]]
- La salida es:
- ![[Pasted image 20240716115932.png]]
- ![[Pasted image 20240716120400.png]]

### GRU
![[Pasted image 20240716120537.png]]

## Transfomers

### Qué son?

- Los transformers usan RNNs y usan MLPs
- Las RNN y LSTM son secuenciales. Y es por esto que dependen del pasado, utilizan el pasado para predecir el futuro.
- Los Transformers no son así, manejan todo en paralelo. No dependen del pasado, ni necesitan predecir el futuro. Esto les permite analizar el contexto no sólo basado en lo pasado, si no también en el futuro, esto significa que pueden tener una mejor visión del contexto al verlo todo a la vez.
- Estándar de rendimiento en una variedad de tareas de NLP
- BERT (Bidirectional Encoder Representations)
- GPT (Generative Pre-trained Transformer)
- Estos modelos son capaces de captar sutilezas del lenguaje y generar texto.

- Ya aprendimos como codificamos texto en numeros:
- Podemos representar las palabras de forma discreta como tokens independientes:
	1. Construir un diccionario de tokens con un indice asignado por ejemplo con el orden alfabetico
	2. O usar one-hot encoding
O puedo usar embeddings, un vector continuo, que tiene multiples aspectos del token, varias relaciones, donde puedo agregar nuevos significados mientras son aprendidos, dependiendo de todo tipo de contextos.

Igual que siempre, el PLN es calcular la probabilidad de una palabra basado en las palabras que están a su alrededor, o el contexto.