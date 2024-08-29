## Técnicas para resolver problemas en IA

- Las investigaciones en IA mostraron que el comportamietno inteligente necesita conocimiento
- Y el conocimiento tiene algunas propiedades indeseables:Cara
	- Es voluminoso
	- Difícil de caracterizar
	- Cambia
	- Comúnmente se organiza de la misma manera como se usará
Las técnicas de IA en general incorporan procesos de búsqueda
Los métodos de busqueda pueden considerarse como arboles de busqueda en los que cada nodo represente un estado del problema y cada enlace representa la relacion entre los estados vinculados
En general, hay reglas que determinan como navegar por el arbol y partes del arbol pueden generarse o expandirse a medida que se activan las reglas.
Hay direcciones asociadas con los enlaces, que dirigen la búsqueda (hacia adelante o hacia atrás)
También hay una estrategia de control para seleccionar las reglas que se pueden aplicar.
Las buenas estrategias de control siempre permiten pasar a otros estados y avanzar sistemáticamente en el proceso de búsqueda

- Estrategias de búsqueda en el espacio de posibles estados
	- Goal-driven- encadenamiento hacia atrás
		- Toma el objetivo a ser resuelto. Ve qué reglas o movimientos legales podrían usarse para generar ese objetivo y determina qué condiciones debens er ciertas para usarlos.
		- Estas nuevas condiciones se convierten en los nuevos objetivos para la búsqueda, se remonta a los hechos del problema.
		- Esto se encuentra a cadena de movimientos o reglas que conducen de los datos a la meta, pero es al revés.
		- Caracteristicas: El objetivo está claramente definido, los datos son escasos, 
	- Data-driven: encadenamiento hacia adelante
		- La búsqueda comienza con los hechos dados del problema y un conjunto de movimientos legales o reglas para cambiar el estado.
		- La búsqueda continúa aplicando reglas a los hechos para producir nuevos hechos, hasta que genera un camino que satisface la condición del objetivo.

Tipos de búsqueda basados en la estrategia de control:
- Algoritmico
	- Tenemos la informacion sobre las operaciones a realizar (generalmente no nos interesa aqui, ya que si tenemos el algoritmo, simplemente lo usamos, no necesitamos IA)
- Búsqueda exhaustiva (búsqueda a aciegas)
	- Exploran el árbol de búsqueda sitemáticamente, pero sin información
- Búsqueda heurística (búsqueda informada)
	- Reducen la búsqueda con información sobre el dominio del problema.
	
Estrategias de búsqueda a ciegas:
- Generate and test
- Breadth First
- Depth first
- Uniform cost search
- Limited depth
- Interactive depth
- Bidirectional search

### Generate and Test

Algoritmo
1. Genera una posible solución (estado o ruta)
2. Prueba para ver si es la solución. Compara con los elementos de un conjunto de soluciones aceptables.
3. Si se ha encontrado una solución, regrese. Si no, vaya al paso.
Desventajas:
	No aprende, no hay comportamiento inteligente, porque no tiene memoria, cuando genera una solución incorrecta, no hay conexión entre la solución fallida y la siguiente solución.
	No recuerda las soluciones probadas y desechadas anteriormente
	No recuerda las experiencias previas
	Se pierde el conocimiento.
- Una mejora del algoritmo es garantizar que una solución nos e pruebe más de una vez. Esto se puede hacer enumerando las soluciones y probándolas en orden.
- Si las soluciones no se pueden enumerar, genere las soluciones al azar, pero mantenga una lista o una matriz con todas las soluciones probadas, para buscar una solución potencial antes de probarla.
- Esa alternativa tiene algunos problemas. Puede llevar tiempo buscar una solución probada cuando la lista crece.
- Si es muy grande la lista, puede ser mejor generar aleatoriamente una solucion no probada
#### Generate and Test mejorado Breadth first
![[Pasted image 20240725115231.png]]
Visitando la primera parte de todas las rutas, podemos verificar cuales nodos ya visitamos y cuales no.

**En breadth-first, una vez que se encuentra la solución, la ruta desde el estado inicial hasta el estado objetivo es la ruta más corta.** Por lo que, por más que la primera ejecución se demora mucho, me asegura el mejor tiempo si sigo usando la misma ruta después.

- Completo
	- Si, inclsuive para arboles infinitos
	- Siempre encuentra la ruta más corta
- Tiempo
	- O($b^{m}$)
- Memoria
	- El número máximo de nodos se alcanza en el nivel "m"
	- En general: $b^{m}$
	- Generalmente "peor" que depth first
### Depth First
![[Pasted image 20240725120212.png]]

Vale recalcar que ambos algoritmos, si tengo alguna forma de conocimiento que guia por donde buscar antes, se vuelve una busqueda heuristica, que lo encontrará más fácil. Como veremos.

## Búsqueda heurística (o informada)

- Búsqueda inicia con información previa
- Las decisiones se basan en la heurística (reglas generales o información limitada)
- Los humanos generalmente tomamos decisiones rápidamente, a veces sin considerar conscientemente por qué se selecciona una opción u otra.
- Del griego "heuriskein", que significa descubrimiento o hallzazgo
- Proporciona informacion para guiar el proceso de búsqueda
- La búsqueda basada en heurística, no siempre garantiza encontrar el resultado más óptimo (la mejor solución de todas), pero obtendremos muy buenos resultados en n tiempo razonable.
- La heurística se usa para resolver problemas complejos donde generalmente tenemos una explosión combinatoria, donde los algoritmos de búsqueda exhaustivos tienen costos inaceptables.
- Entonces, utilizamos heurística para "seleccionar" qué nodo expandir o explorar explorar
- Aparece como una función que se evalúa con base en información especifca para el contexto o problema en cuestión
- La solución del problema consiste en maximizar o minimizar una función
- Por ejemplo, en redes neuronales, la heuristica es el gradiente descendiente.
- Los algoritmos inteligentes deben poder regresar al mejor paso posible, eso es lo que los hace inteligentes
- Recordar también, de nuevo, que los algoritmos inteligentes nunca se caen, siempre dan una respuesta, así sea erronea. Esto es porquen o están explicitamente programados para encontrar la respuesta, si no que hacen una busqueda

