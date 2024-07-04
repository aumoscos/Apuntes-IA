## IA - ML - DL
La inteligencia artificial trae varias tecnologías nuevas y campos, como lo son Bio-computación, Vida artificial, lógica difusa, Computación enjambre, Minería de datos, etc.
Generalmente lo que se cumple con estas son problemas que no pueden ser resueltos de manera precisa o matemática.

### [[Machine Learning]]
Uno de estos campos es el Machine Learning (ML) o aprendizaje autónomo.
Este busca técnicas para que los sistemas reproduzcan comportamiento inteligente sin ser explícitamente programados para hacerlo.
**Vale recalcar que es un error decir que replica la inteligencia humana, se está muy lejos de esto.**

### [[Deep Learning]]
El deep learning es un subcampo del Machine Learning, que a su vez es un subcampo de la inteligencia artificial. La diferencia recae en que este usa los algoritmos de una manera muy específica para aprender de mejor manera. "Para hacer lo que es natural para los humanos: aprender de los ejemplos."
Las [[Redes neuronales]] y los [[Transformers]] son ejemplos de Deep Learning

### [[IA Generativa]]
Subcampo del Deep Learning
Crear contenidos semejantes a los generados por humanos. La idea es no solo aprender de ejemplos como humanos, si no poder replicar lo que ellos hacen.
![[Pasted image 20240521113600.png]]

## Definición de Inteligencia Artificial
### Objetivos a largo plazo
-  Desarrollar sistemas que alcancen el nivel de "inteligencia" similar/comparable/mejor que el de los humanos.
- En algunas aplicaciones ahora es posible, pero aún no es posible en muchas otras...
### Objetivos a corto plazo
- En **Tareas específicas:** desarrollar sistemas que alcancen niveles de "inteligencia" similar/comparable/mejor que el de los humanos.
- Hoy existen sistemas que realmente superan a los humanos, en algunas órdenes de magnitud ...
- Dentro del contexto de los objetivos a corto plazo: 
	- La IA no busca "simular" la inteligencia humana
	- Pero busca generar resultados similares.

Como ejemplo, al momento de buscar el vuelo para los humanos, no se intentó replicar la fisiología de las aves, se buscó replicar el resultado final, con herramientas como son los aviones.

### Cuales son las ciencias que han contribuido al desarrollo de la IA?
- La filosofía ha dado una gran contribución, principalmente la idea de que en un proceso, debe haber una entrada que produce una salida. Esto ha sido inmensamente importante para la computación en general, y aún más para la Inteligencia Artificial.
- La matemática y ciencias exactas han ayudado muchísimo, y son bajo lo que funcionan las inteligencias artificiales, las primeras IAs buscaban demostrar teoremas matemáticos, y las tecnologías actuales utilizan funciones matemáticas para su funcionamiento, como matrices, funciones, derivadas, etc.
- La psicología ayuda dado que analiza el comportamiento humano, y nos da datos sobre este.
- La lingüística nos da las reglas y estructuras necesarias que los modelos de lenguaje siguen
- Ciencias computacionales, dan todas las tecnologías y avances necesarios con los que las inteligencias artificiales son creadas.
- La medicina nos da ciertos modelos bajo los cuales se toman inspiración varias tecnologías, por ejemplo, las redes neuronales tienen una arquitectura basada en neuronas reales.
## Cuál es el propósito de la IA?
Lograr que el comportamiento de las soluciones y disciplinas que ya practicamos y conocemos sean inteligentes, elevarlas para que la toma de decisiones humanas sea complementada bajo datos. 
**Apoyar al ser humano en sus decisiones.**
![[Pasted image 20240521121515.png]]

## Machine Learning- Aprendizaje Autónomo
### Algoritmos de aprendizaje autónomo:
- [[Aprendizaje no supervisado]]
- [[Aprendizaje supervisado]]
- [[Aprendizaje por refuerzo]]
- [[Aprendizaje auto-supervisado]]
- [[Aprendizaje híbrido, mixto]]
- [[Aprendizaje por transferencia]] (No son algoritmos de aprendizaje como tal, más bien utilizan aprendizaje previo de otros algoritmos para construir sobre ellos.)
### Aprendizaje Autónomo - intuiciones
Si tenemos un programa diseñado para multiplicar números enteros, el programa recibe como entrada números y se obtiene como salida el producto de éstos.

Aquí no hay inteligencia.

Sin embargo, si queremos un algoritmo que "aprenda" a reconocer números nones sin darle su definición
En lugar de darle la definición, le damos ejemplos de números impares y pares indicando al algoritmo cuáles corresponden a cada categoría.
El programa por si mismo debe "descubrir" el concepto de impar y, eventualmente aplicarlo a nuevos ejemplos no vistos antes.

![[Drawing 2024-05-21 12.28.38.excalidraw]]

Esto es [[aprendizaje supervisado]], dado que "superviso" su aprendizaje por medio de darle las entradas y las salidas como entrada, para que encuentre la relación. 


Además, hay [[Aprendizaje no supervisado]], para cuando no tengo las salidas de lo que quiero. Es decir, en este caso solo se le darían los nones, para que aprenda qué características tienen en común