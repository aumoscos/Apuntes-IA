## TF-IDF
### TF
Frecuencia de términos: # de veces un termino aparece en un documento en comparación con el # total de palabras en el documento

### IDF
fRECUENCIA INVERSA DE DOCUMENTOS: pORPORCION DE DOCUMENTOS EN EL CORPUS QUE CONTIENE EL TERMINO

IDF = log (# de documentos en el corpus/# de documentos en el corpus que contienen el termi)

## Tipos de Embeddings
- Estadísticos:
	- Son numeros únicos que representan las palabras. Estos pueden ser valores pre-entrenados de las palabras, que luego se podrian usar para entrenar otros modelos.  
	- ![[Pasted image 20240711112601.png]]
	
- Contextual:
	![[Pasted image 20240711112821.png]]
	- El entrenamiento se hace con documentos y definiciones donde se usan las palabras, para poder hacer los embeddings basado en cómo son usadas las palabras dependiendo del contexto.
## Modelado del lenguaje
- Recordar que las RNN usan informacion secuencial y time-steps, es por esto que son recurrentes, se usa la misma red una y otra vez, realizan la misma tarea para cada elemento de la secuencia, y la salida depende de los cálculos anteriores. Esto preserva la memoria, es en la secuencia que está el factor de interés.
- Vale recalcar que mientras más larga es la ventana, más propensa es a perder memoria. No recordará lo primero que estaba en el documento.
- Idealmente las RNN podrían utilizar la secuencia de información arbitrariamente larga del pasado, pero en la practica, se limitan a unos pocos pasos en el pasado

## Aprendizaje RNN

![[Pasted image 20240711113505.png]]
![[Pasted image 20240711113512.png]]
- Despues de calcular un $h_{t}$, este será $h_{t-1}$ en el siguiente timestep![[Pasted image 20240711114759.png]]
										![[Pasted image 20240711114835.png]]


![[Pasted image 20240711115043.png]]

![[Pasted image 20240711115201.png]]

Mira nomas las diapositivas de la clase 16 xd

## BPTT - Back Propagation Through Time
![[Pasted image 20240711115807.png]]
![[Pasted image 20240711120013.png]]
Vale recalcar que en el momento de calcular el error: 
- Solo afectan los pesos actuales y del pasado, los del futuro no aportan al error
- Los pesos que conectan con otros y, no afectarán al de este y, por ejemplo, si estoy calculando yt+1, el W de yt ni el de yt-1 aportarán

Procedimiento para el algoritmo BPTT
1. Calculamos el error utilizando la salida actual y la salida
![[Pasted image 20240711120457.png]]

![[Pasted image 20240711120506.png]]
![[Pasted image 20240711120859.png]]

### Desvanecimiento del gradiente
![[Pasted image 20240711121230.png]]
![[Pasted image 20240711121237.png]]

Las RNN son más efectivas cuando el valor que se desea encontrar está cercano al valor importante.
Mientras más aumenta la brecha, le cuesta más a la RNN conectar la información.
Por ejemplo, si tengo contexto al inicio de la oracion que necesito relacionar con algo al final de la oracion, el desvanecimiento del gradiente va a causar problemas al momento de conectar la informacion.

## LSTM 
![[Pasted image 20240711121709.png]]
![[Pasted image 20240711122301.png]]
