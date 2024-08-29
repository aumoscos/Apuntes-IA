## Redes neuronales recurrentes
### Modelado del lenguaje (NLP)
- Esto no es necesariamente sólo texto, si bien iniciaremos analizando texto, esto puede llevar varios tipos de lenguaje. 
- Las técnicas de NLP son muy complejas y dificiles de descubrir, pero son soluciones tan elegantes matemáticamente que han tenido efectos en distintos campos, ya que se utilizan para transformar un simbolo que por su cuenta no tiene sentido, a algo con contexto.
- Entrando por la parte del texto, este tipo de redes permiten predecir; por ejemplo, cual es la siguiente palabra en una oración. 
- Una oración es un conjunto de símbolos, que como humanos entendemos qué significan en su contexto. Los modelos no pueden entender lo que esto significa, pero si son capaces de relacionar cada simbolo con su contexto, y basado en los datos con los que es entrenado, predecir cuál es el siguiente simbolo más probable, es de esta manera que puede predecir palabras, y escribir reportes. En estas cosas tiende a ser mejor que los humanos, ya que está comparando con todo su conocimiento.
#### Aplicado
- La base del modelamiento de lenguaje se denomina n-gram
- Un n-gram es un conjunto de n palabras consecutivas
- Por ejemplo, en la oración: "Estoy escribiendo un ...", tendríamos los siguientes tipos de n-grams:
	- unigrams: "Estoy", "escribiendo", "un", "..."
	- bigrams: "Estoy escribiendo", "escribiendo ..."
	- trigrams: "estoy escribiendo un", "escribiendo un ..."
	- etc.
	- La razón para los n-grams es que no siempre usaremos 1, se puede usar más si asumimos que un conjunto de símbolos siempre irán juntos, basado en el contexto.
- Esencialmente es la cantidad de palabras en secuencia que vamos a dividir en tokens, es decir representar en números como parte de la entrada. 
- En el modelado del lenguaje con n-grams recopilamos la frecuencia del uso de los diferentes n-grams en el texto, y usamos esa frecuencia para predecir la siguiente palabra
- Un reto que enfrentan los modelos de lenguaje con n-grams es "sparsity", en particular cuando no hay suficientes datos en un corpus para modelar ele lenguaje con prescisión (especialmente cuando n aumenta). Esto tambien da problema con el one-hot encoding, porque genera un pico, tendremos una matriz donde tenemos un 1 y el resto será 0, donde si multiplicamos una matriz por este vector, se apagará todo menos uno.
- Ha varios metodos de representacion que mejoran esta debilidad: Bag-of-words - BoW, word embeddings, binary encoding, Tf, latent semantic analysis, Word2Vec, etc.
### Embeddings

![[Pasted image 20240709122918.png]]

Qué es un embedding?
- Es una representación numérica del texto, donde las palabras con igual significado tienen una representación similar. 
- Es decir, la representación numérica de una palabra debe representar su significado dependiente de lo que está a su alrededor, una palabra no debe tener un embedding único si su significado puede variar.
- Es un vector d-dimensional para cada número o índice de representación de cada palabra.
- Si tenemos un diccionario de 10000 palabras, necesitamos 10000 índices. Estas palabras son el Corpus, son las palabras que conoce el modelo.
- Cada palabra tiene un índice único y cada índice tiene un vector embedding.
![[Pasted image 20240709123412.png]]
Cojo cada palabra, a cada palabra le creo un índice, y cada una le hago un embedding, que será un vector. En Transformers ese vector será de tamaño 512.
La oración será un Tensor, dado que tendrá una matriz de estos vectores.
Los tokenizers agregarán dos tokens, un clasificador y un separador.
Toda la información se encuentra en el Token inicial, el Clasificador, y el Separador esencialmente indica que hasta ahí llega la oración.
