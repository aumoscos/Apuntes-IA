## Transformers

### Qué son?
![[Pasted image 20240718114251.png]]
![[Pasted image 20240718114304.png]]
La mitad de la izquierda es donde genera el análisis y la probabilidad, la parte derecha es la que genera la parte secuencial, donde predice el futuro. Por lo que muchas aplicaciones solo usan la primera mitad.

Seq2Seq significa que se da como entrada una secuencia, y la salida será otra secuencia.
![[Pasted image 20240718115536.png]]
![[Pasted image 20240718115555.png]]
Internamente, tiene varias capas de codificacion y decodificacion en paralelo, cada una será una copia de lo mismo, pero al trabajar en paralelo, pueden trabajar correctamente a lo largo de toda la secuencia.
![[Pasted image 20240718115850.png]]

![[Pasted image 20240718120427.png]]

La attention lo que me permite es superponer una palabra con todas las demas palabras, y analizar la probabilidad de sus significados dependiendo de esto, hago esto con cada una de estas palabras, relacionando cada una con todas las demas.
![[Pasted image 20240718120601.png]]
Tengo 3 matrices, las keys, querys
Inicialmente hago la multiplicacion de la palabra que estoy multiplicando la palabra por la matriz k, y eso me da una matriz de keys, es decir los valores probables.

![[Pasted image 20240718120934.png]]
Una vez que tenemos las keys, multiplicamos el numero por la matriz Q, esto nos da un Query.
Luego, realizamos el producto punto entre Q y K, y esto nos va a dar el coseno, es decir una metrica de similitud.
![[Pasted image 20240718121303.png]]
![[Pasted image 20240718121320.png]]

- Un ejemplo, si quiero filtrar peliculas de ciencia ficcion, K es el contexto, todas las peliculas, Q es el query, ciencia ficcion, V es un valor, star trek, por ejemplo.
![[Pasted image 20240718121432.png]]
![[Pasted image 20240718121447.png]]

Entonces, hago la multiplicacion de todas las salidas de la multiplicacion del query por la matriz de valores, y sumados estos, serán la salida.

![[Pasted image 20240718121557.png]]
La versión original del transformer realiza la operacion que acabamos de mencionar 8 veces, es decir, con 8 cabezas. Esto se conoce como auto atencion con multiples cabezas. La idea de esto, es que se obtienen 8 salidas, y esas 8 salidas entran a una MLP, que decide cual salida es la mejor.

![[Pasted image 20240718122043.png]]

Cada palabra entra a la capa de self-attention y da como salida un vector, uno por cada palabra. eso, pasa por la MLP, y sigue al siguiente encoder y al decoder respectivo.

Cada matriz KQV, es una matriz que tiene los metros W. Vale la pena mencionar que tengo  yo que definir el tamaño de estas matrices dado que estas matrices limitaran o modificaran el tamaño de la salida. En el transformer original, con el embedding de 512, y las matrices KQV 64, por lo que el tamaño resultante es de 512x64

En detalle, lo que se hace, es multiplicar el q de la palabra por K, y eso dará un score de similitud. Esto se hace de la palabra con todas las demas palabras, q1k1, q1k2, q1k3, etc.
Se hace el remdimensionamiento, dividiendo por la raiz  del tamaño, limitar con el softmax, y el softmax se multiplica por los valores, y se suman las sumas de todas las palabras.
Luego, se repite el proceso con la siguiente palabra.
Vale recalcar que en practica la idea es que esto se hace con todas las palabras en paralelo.


KQV son los parametros que se aprenden
Key= Oracion completa
Values= De manera puntual cuales serian los parametros de ese contexto, las palabras en secuencia con sus correspondientes valores.