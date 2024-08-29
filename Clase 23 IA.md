Para que mi solución sea inteligente, el método de la representación es:
- Expresivo
	- Permite representar toda la información necesaria y la experiencia.
	- Proporciona un esquema natural para representar el conocimiento requerido.
- Eficiente
	- Para permitir la ejecución eficiente de código en una computadora.
	- En general permitir resolver no solo problemas cuantitativos, sino también cualitativos.
	- Organizar grandes y diferentes tipos de conocimiento, y permitir implementar algoritmos de búsqueda.
- Esto es, el método de representación del conocimiento debería permitir:
	- Inferir nuevos conocimientos a partir de hechos básicos.
	- Representar principios generales, así como situaciones específicas.
	- Capturar el significado semántico complejo.
	- Representar el meta-conocimiento.

### Esquemas de representación del conocimiento:

1. Representación lógica
- Utiliza expresiones lógicas formales para representar el conocimiento.
- Cálculo del predicado de primer orden.

2. Representación procedimental
- El conocimiento se representa como un conjunto de instrucciones.
- Reglas tipo: SI - ENTONCES.
- Un reto de estas, es el encapsulamiento. Si las  reglas se encuentra encapsuladas entre si, una siguiente regla puede no conocer lo que está encapsulado en otra regla. Esto puede causar contradicciones, o lazos como If x Then z, If z Then x

3. Representación en red
- El conocimiento se captura en forma de grafos, redes, mapas.
- Los nodos representan objetos, unidades de procesamiento o conceptos, y los enlaces representan relaciones o asociaciones entre ellos.
- RN, redes semánticas, gráficos conceptuales, mapas cognitivos.

4. Representación estructurada:
- Es una extensión de la representación de la red.
- Los nodos son estructuras complejas que contienen "ranuras con valores asociados"
- Scripts, frames, objetos.

La representación del conocimiento debe permitir no solo capturar y razonar sobre los aspectos cuantitativos, sino también aspectos cualitativos de un problema.
(Cualitativo se refiere más que nada a las relaciones y estados de las cosas, Cuantitativo se refiere a la cantidad de cosas de cada tipo.)

### Proposiciones

- Las proposiciones en el cálculo proposicional, y los predicados se pueden usar para representar y razonar sobre las propiedades y relaciones de cualquier objeto.
- Son hechos que estoy capturando.
- "Hoy está nublado", "Sam mi perro es inteligente", "Domingo es un día de descanso."
- Para poder inferir de estas proposiciones, hay que acceder a los elementos individuales de la porposición como tal, esto se hace creando predicados

Por ejemplo, si tenemos P = Hoy está nublado
Podemos crear un predicado "clima", con el que podemos describir la relación entre la fecha y el estado del clima en esa fecha, así: clima(hoy, nublado).

Aún más, podemos generalizar el día y el estado cómo ?: clima(X,Y)

Con esto, para poder inferir nuevas leyes, debemos utilizar y aplicar leyes de inferencia.
Sintáxis:
- Los simbolos en el calculo del predicado son elementos sintacticos y no se pueden reducir
- Letras (mayúsculas para constantes minúsculas para variables)
- Digitos del 0 al 9
- El simbolo "_"
- Símbolos no legales
	- 5ases, ab ^  5
- Los símbolos se usan para referirse o nombrar objetos, propiedades o relaciones en el mundo real
	- g(j,k), gusta (jorge, kathy) - son formalmente equivalentes
- Paréntesis, coma, y punto se usan para componer fórmulas bien formadas (wff) de expresiones
- Los símbolos pueden representar variables, constantes, funciones o predicados.

### Reglas de inferencia

- Los símbolos y sus estructuras, en el cálculo de predicados, proporcionan las bases para la inferencia artificial formal en la lógica matemática.
- La capacidad de inferir nuevas expresiones, a partir de un conjunto de afirmaciones verdaderas, es la clave en el cálculo de predicados.
- Las nuevas expresiones son correctas porque son consistentes con las interpretaciones originales representadas con símbolos.
- Cuando una interpretación hace a una afirmación verdadera, se dice que la interpretación satisface la afirmación.

Para inferir **necesitamos** que las variables estén universalmente definidas.
