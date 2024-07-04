## Qué hace a los sistemas inteligentes?
Cumplen problemas complejos, 

Siempre toman una decisión. Los programas inteligentes toman una decisión así el problema esté incompleto, así hayan datos erróneos, así sea algo nuevo. El programa inteligente es capaz de adaptarse y siempre llegar a algo, no se cae, no tira error. Eso los diferencia de programas convencionales, donde si entrego un float en lugar de un int, acaba ahí.

## Introducción al aprendizaje autónomo (machine learning)

### Aprendizaje con refuerzo

![[Drawing 2024-05-23 11.34.55.excalidraw]]

Se le da al algoritmo una recompensa por tomar el camino correcto, diferente de [[PID]].

## Aprendizaje supervisado - Algoritmos lineales: [[Regresión lineal, de una variable]]

**Nota:** Diferencias entre Estadística e IA. En caso de la Estadística, se provee un modelo y datos, y el modelo da los resultados, en caso de no ser correcto, se cambia el modelo. En caso de la IA, se dan los datos, y el algoritmo crea el modelo. En caso de haber errores, se dan más datos.

Training set: Son los datos, ejemplos que se dará al algoritmo.
Donde:
- m= Números de ejemplos para entrenamiento
- X = variable de entrada / "features"
- Y = variable de salida / "target"
La idea es tener la mayor cantidad de Features, la mayor cantidad de filas, no de columnas. Queremos que los datos sean de buena calidad, y mientras más tenemos, de mejor calidad el resultado.

La función de error queda a decisión del programador, no hay una correcta, y dependerá del problema a mano.

**Recordatorio:** Error 0 es sospechoso, puede existir overfitting, es decir, memorizó todos los ejemplos, y está usando eso para resolver el problema exactamente. Por lo que no sabrá como reaccionar ante datos nuevos

Para una función, como: J(w0,w1)

Deseamos: el mínimo (w0,w1)

Procedimiento:
- Empezar con valores iniciales w0,w1
- Actualizar paso a paso w0 y w1 hasta minimizar j(w0,w1)
- Hasta posiblemente llegar al mínimo global.
Cómo minimizamos w0 y w1?

- En ML, el algoritmo descubre (aprende) los parámetros que definen hw(x) desde los datos de entrenamiento y "ajusta" el modelo de forma "iterativa", hasta minimizar el error con respecto al modelo deseado.
- Una vez entrenado el modelo hw(x), se espera que sea el "correcto."

## Aprendizaje supervisado: Gradiente descendiente
- A través del GD podemos calcular la dirección y la magnitud de los peque;os cambios en los parámetros, y así ajustar de forma iterativa el modelo.
- Ese calculo se realiza a través de la derivada de la función de costo
- De manera queda corección o ajuste del parámetrow1 seria:
	w0 nuevo = w0 anterior - a (d/dw0)J(w0)


![[Pasted image 20240528111259.png]]