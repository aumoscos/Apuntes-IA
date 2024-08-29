==**El razonamiento está dado por los símbolos establecidos, pero dado que el método no sabe lo que los símbolos significan, es necesario que estén contextualizados, en este caso lo hacemos con paréntesis, ingresandolos en contextos y subcontextos. Las variables en distintos contextos y subcontextos no necesariamente significan lo mismo a pesar de que tengan el mismo nombre de variable. Es para esto que utilizamos unificación, para no mezclar variables.**==

## Unificación.
![[Pasted image 20240808112357.png]]

De nuevo, necesitamos que todas las variables sean universalmente cuantificadas. Y si existen variables existencialmente cuantificadas, son las primeras variables que hay que reducir. Dado que estas están infringiendo el proceso de inferencia.
![[Pasted image 20240808112516.png]]
![[Pasted image 20240808112524.png]]
![[Pasted image 20240808112912.png]]
**Ojo:** Las variables siempre se expresan entre {}, por ejemplos, si reemplazo X1 por X2, se expresa {X1/X2}.

![[Pasted image 20240808113015.png]]
(Recomendado hacer las subtituciones paso a paso, si intento saltar las partes intermedias luego me equivoco.)

![[Pasted image 20240808113507.png]]

En caso de que no puedas hacer una substitución porque habría  un loop, entonces no son sintácticamente reducibles.

![[Pasted image 20240808113930.png]]
![[Pasted image 20240808114131.png]]
![[Pasted image 20240808114209.png]]
Para poder hacer una unificación o substitución de una instancia existencial, **debo** usar una función Skolem

## Teorema de Resolución.

- El principio de resolución fue introducido en 1965 por R. Robinson.
- Es una técnica para probar teoremas usando cálculo de predicados.
- Es un método de inferencia sólido, correcto y completo.
- Proporciona una forma de encontrar contradicciones en una base de cláusulas con un conjunto mínimo de sustituciones.
- Goal Driven.
Pasos:
1. Convertir las aserciones o axiomas en forma de cláusula. (Formato o representación standard. Significa conjunción de disyunciones.)
2. Agregar la negación de lo que debe probarse (la hipótesis), en forma de cláusula, al conjunto de axiomas originales. 
3. Resolver estas cláusulas, produciendo nuevas cláusulas que lógicamente provengan de las originales. 
4. Producir o encontrar contradicciones, genere la cláusula vacía. 
5. Extraer el resultado de las sustituciones.
(Nota, por buenas prácticas, se busca empezar por la clausula que representa la hipótesis, en caso de que no se pueda, se debe intentar hacerlo lo antes posible.)
