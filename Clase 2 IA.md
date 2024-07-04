## Estado del arte AI - ML
### [[Graph Neural Networks]]
Las GNN aplican una serie de transformaciones a los nodos de grafo, basandose en sus propios atribtos y en la información de sus vecinos.
Permite analisar los detalles de la causa y efecto. Los grafos permiten ver como un nodo afecta a el siguiente segun los edges de este. Que es similar a como funciona una red neuronal. Entonces se puede representar un nodo como una capa de la red neuronal, conectado con la siguiente.

Con GNN puedes hacer predicciones de todos los caminos posibles y hacer una predicción o conocer el mejor camino. 
Te permiten definir un grafo entero para entenderlo, o un nodo especifico para saber cual sera el efecto del grafo sobre ese unico nodo, o incluso se pueden estudiar las conexiones.

### [[Federated Learning]]

Permite entrenar un algoritmo a través de multiples dispositivos descentralizados o servidores sin necesidad de compartir los datos entre ellos.

En lugar de llevar los datos a un servidor central, el AF lleva el modelo a los datos, permitiendo que el modelo aprenda de esos datos en su ubicacion original.

En lugar de llevar los datos al modelo, llevo el modelo a los datos. Similar al procesamiento distribuido. Pero todos los servidores desarrollan la misma tarea, pero con sus propios datos. Todos los servidores comparten los mismos parametros y el mismo modelo, pero entrenan con sus propios datos. 
El momento de terminar el entrenamiento, se comparten 

### [[Procesamiento de Lenguaje Natural (PNL)]]
Es una de las tareas más difíciles para la AI, dado que es necesario contexto para entenderlo, dado que la computadora no es capaz de entender lenguaje, solo trabaja con números. 
Es una cosa identificar el significado de una palabra isolada, pero en el lenguaje natural, las palabras cambian de significado dependiendo de las palabras que están alrededor de esta.

Este problema se solucionó con la creación de [[Transformers]], y con el sistema de "atención" que tienen. La atención calcula una distribución probabilística del significado de cada palabra en el texto basado en lo que está tanto antes como después de la misma, y con eso predecir o identificar cual será el significado que queda mejor en ese espacio.

Para otros usos se utiliza un tipo de redes neuronales que analizan patrones secuenciales, pero estos solo ven "el pasado", ven lo que está antes de la palabra, pero no después, los transformers con atención si usan el "futuro" para resolver sus problemas.
 
- [ ] (Leer attention is all you need, paper de donde sale todo este chiste)

Sin embargo, no entiende realmente el lenguaje, entiende la combinación de los símbolos, entiende cómo usan los humanos generalmente cada símbolo y en qué contexto, porque es en lo que está entrenado. Pero por esto no es perfecto, puede "alucinar", si no encuentra algo que alguien ya ha escrito con el contexto necesario, se inventará algo, o usará cosas en el contexto incorrecto, dependiendo de lo que se le pida.

Ejemplos incluyen generación de resúmenes, responder preguntas, clasificar texto, Clasificar texto.
BERT y GPT son ejemplos de transformers.

## Autonomia en los autos

Conducción de autónoma, implica un algoritmo complicado, ya que los autos tienen diferentes reacciones dependiendo de la situación y los obstáculos que se encuentra, por lo que los modelos tienen que ser sofisticados para navegar a través del tráfico en tiempo real
Dado el AI generativo, los autos ya no necesitan un mapa, pueden navegar por su cuenta.

## Asistentes virtuales

Alexa, Siri, Google Assistant... etc.

Vienen del PNL y por lo tanto de Transformers, se centran en poder procesar habla, texto, imágenes, audio, etc. Importante para muchos casos es el conocer cómo utilizar los APIs de modelos como lo son chatGPT etc.

## Detección de fraude.

La mejor forma de detectar fraude, especialmente cuando es plagio que utiliza IA, es utilizar IA que lo detecte. Identifica los patrones y comportamiento anómalos. 

## Entretenimiento

El desarrollo de IA está en el estado que está gracias al avance en entretenimiento, especialmente en videojuegos, ya que estos impulsaron el desarrollo de GPUs y su proliferación, que han sido empujados gracias a la industria de videojuegos.

También han habido avances gracias a la ambición de usos de [[IA generativa]] para usos como crear mejores avatares más precisos, experiencia personalizada o espectadores, sincronización de audio y video, transcripciones, etiquetas, las cámaras han aprendido a interpretar el lenguaje corporal humano.

Vale notar que la misma célula que se dio en el inicio de la IA, es la misma que se usa hoy en dia en modelos como transformer e IA Generativa.

## Reconocimiento visual

Clasificación de imágenes en función de las ubicaciones en fotografías, rostros, o eventos, fechas, etc.

Predice intenciones.

## Detección de noticias de fraude.

Personalizar noticias, detección de noticias fraudulentas.
Se dice que los algoritmos de hoy en dia entienden la psicología humana mejor que los mismos humanos. Es por esto que funcionan tan bien a veces los algoritmos que te intentan ofrecer cosas de tu interes, como Amazon, YouTube, etc.

Hoy en día es muy frecuente la propagación de noticias falsas por intenciones políticas, y muchísima gente cae en ellos, por lo que IA que las pueda detectar es muy importante

## IA explicable

Es importante para la aceptación de los resultados de una Inteligencia Artificial que sea capaz de dar un razonamiento para estos, por ejemplo, en el caso de usos médicos, es necesario que un doctor pueda preguntar a la IA por qué identificó  o no un tumor. 

La IA explicable usa algoritmos complicados para poder explicar de donde saca conclusiones. Usar un mapa para mostrar en donde encontró patrones específicos, o el tren de pensamiento, etc.
Es importante tomar en cuenta que la IA no entiende necesariamente el problema, solo sigue patrones, por lo que hacerlo explicable es sofisticado.

## Reconocimiento de imágenes.
 
 Una CNN reconoce lo que existe en la imagen, una RNN crea la descripción

## Generación de imágenes

Una IA funciona recibiendo ciertos datos de entrada, y un resultado esperado, y de lo que se encarga la red neuronal es de buscar una función matemática que transforme la matriz numérica de la entrada, en lo más acercado posible al resultado esperado.

## Redes generativas adversarias

Estas redes neuronales permiten generar nuevos datos utilizando datos existentes de tal manera que el nuevo producto se asemeje al original.

## Convergencia de IoT e IA

Los sensores del Internet de las cosas generan una cantidad ***masiva*** de datos, estos datos pueden ser utilizados para entrenamiento de IA que puede entrenarse para muchas cosas, entre ellas, devolver a la funcionalidad del mismo IoT

## Qué es IA?

Parte de la ciencias de la computación que se enfoca en la creación de hardware y software con comportamiento inteligente

Se refiere a las técnicas que permiten a los sistemas realizar tareas como la percepción, razonamiento, y comportamiento inteligentes

Buscamos técnicas que permitan a las maquinas realizar tareas que en algunos casos son mejor realizadas por los humanos.








