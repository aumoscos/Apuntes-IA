## Búsqueda Heurística

Dado que los algoritmos heurísticos exploran el espacio de soluciones. Pueden ser considerados una combinación de los algoritmos anteriores.
Por ejemplo, pueden ser vistos como una combinación de breadth-first y depth-first, ya que dependiendo del estado actual, puede decidir primero a un nodo adjacente o ir primero a un hijo. 
Por lo tanto, su patron de busqueda no es predecible, ya que depende de las decisiones pasadas.

### Hill Climbing.

Es un algoritmo heurístico que prueba y descarta soluciones pero con información previa. Es como un Generate and Test con heurística.
- Desde el procedimiento de prueba, hay una retroalimentación para ayudar a generador de soluciones decidir, en qué direción ir a continuacion o si es necesario cambiar de dirección de búsqueda en el espacio de soluciones.
- Avanza en la búsqueda del estado objetivo en función del mejor estado anterior, es como "subir" a la cima de una colina, continua buscando hasta que el valor heuristico deja de mejorar.
![[Pasted image 20240730114422.png]]
- Los algoritmos heurísticos como hill climbing son locales. Porque deciden qué hacer a continuacion, basándose sólo en las consecuencias de sus acciones inmediatas
- No encuentran "LA mejor" solución
- Pueden quedarse atrapados en un nodo o nodos que no son el objetivo, como un minimo local.
#### Desventajas

Máximo local
- Es el mejor estado o nodo en comparación de sus vecinos, pero no es el mejor entre todos, puede ser que más adelante el valor vuelva a subir hasta un punto más alto.
Meseta
- Es un área plana del espacio de búsqueda en la que todos los estados vecinos tienen el mismo, o similar valor.
Acantilado
- Es un tipo especial de máximo local, que es imposible de cruzar con movimiento simples. Donde puedo variar entre un muy buen valor a un valor muy malo en un solo paso, repetidamente
### Simmulated Annealing

Annealing - Recocido fisico
- Las sustancias físicas se funden y luego se enfrían gradualmente hasta que se alcanza un estado sólido
- El objetivo es producir un estado de energía mínima
- El recorrido simulado es una version mejorada del algoritmo hill climbing
![[Pasted image 20240730120025.png]]
- El recocido simulado difiere del algoritmo hill climbing en 2 aspectos:
	- Se aceptan movimientos a estados peores que el estado actual
	- El estado actual y el mejor estado del pasado se deben almacenar, para que el algoritmo pueda regresar al mejor estado y seguir la busqueda.
### Best-First Search

Es un algoritmo que combina los anteriores. 
- En breadth first, la intencion es no quedar atrapado en caminos sin salida
- En depth first es que no todas las ramas deben expandirse
- Si combinamos ambos, podemos seguir un camino a la vez, pero cambiar de ruta cada vez que aparezca una mejor opción.
![[Pasted image 20240730120328.png]]
No es Greedy search, dado que greedy search es f(n)=h(n)
Ni óptimo ni completo, ya que no usa el pasado.
Tampoco es Uniform-Cost, que es f(n) = g(n)
Óptimo y completo, pero no tan eficiente.

Los best search tienen forma f(n) = g(n) + h(n). Utiliza tanto el presente como el pasado.
![[Pasted image 20240730121201.png]]

![[Pasted image 20240730121224.png]]
==**VA A HABER UN PROBLEMA DE COMO APLICAR BEST FIRST EN UN ENTORNO EN EL EXAMEN**==

## Fronteras

