
## Transformers - Codificación de posición de embeddings.

Al momento de hacer los embeddings de una oración, si tenemos dos ( en el transformer serán 512) elementos en el embedding, tendremos cada palabra, con una conexión a cada elemento, y a cada una de estas conexiones se inicializará un peso, esto se pasará a la función de umbral de cada elemento, y multiplicado por el valor de la palabra, pasado por la función de umbral, se tendrá un valor, y saldrá un vector con todos los valores que salen de las funciones. 
Al final, se tendrá una matriz, donde se tendrán los vectores, de cada uno de estos tokens.
Vale recalcar que el eos también pasa por el proceso.
## Embeds de posición.

Se utilizan funciones de Seno y Coseno para dar una representación continua, alternando dependiendo del orden de las palabras, por ejemplo, las pares usarán un Seno, las impares un Coseno, pero se cambia la frecuencia para que los valores no coincidan, por lo que uso tantas funciones seno/coseno como tokens tenga.
Puede ocurrir que dos palabras tengan el mismo valor de posicion. Pero como se tienen distintas frecuencias, el código será distinto.

## Métricas de evaluación del modelo

La evaluación del modelo y los parámetros de la arquitectura:
- Calidad (presición) de la predicción:
	- Una forma de medir precisión es a través de la Matriz de Confusión, que luce así
	- ![[Pasted image 20240723114909.png]]
	- Un error falso positivo se da cuando el modelo predice la clas 1, pero en realidad es la clase 0 (Error tipo 1)
	- Un error falso negativo se da cuando el modelo predice la clase 0, pero en realidad pertenece a la clase 1 (Error tipo 2)
	- El modelo perfecto clasificaría todas las clases correctamente: todos los 1 (o verdaderas) como 1-TP y todos los 0 (o falsos) como 0-TN. Entonces tendríamos FN = FP = 0

- Impactos de los vlores de umbral (interpretación de la salida):
1. Valor umbral más alto
	- Supongamos que P(y=1)>0.7
	- El modelo es más restrictivo cuando se clasifica como 1 y, por lo tanto, se cometerán más errores negativos falsos
2. Valor umbral inferior:
	- Supongamos que P(y=1)> 0.3
	- El modelo ahora es menos estricto y estamos clasificando más ejemplos como clase 1, por lo tanto, estamos cometiendo más errores positivos falsos.
Vale recalcar que mientras más alto el valor de umbral, más preciso es, y filtrará más datos, pero puede causar más falsos negativos. Y viceversa.

![[Pasted image 20240723115710.png]]

## Otras técnicas para resolver problemas en IA

- Comportamiento inteligente
	 - Conocimiento previo
	 - Búsqueda: todos los algoritmos son de búsqueda
	 - Abstracción: No lidia con todo el problema arbitrariamente, se concentra en partes específicas para el problema.