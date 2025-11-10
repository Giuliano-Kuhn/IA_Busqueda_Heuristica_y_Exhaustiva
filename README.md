##Contexto

Esta es una entrega para una materia de la Universidad XXI, con la que se trata las busquedas Exhaustiva y Heuristica con una orientacion hacia la Inteligencia Artificial.

##Situacion Problematica

El problema principal Es el de una planta industrial destinada a la fabricación de motores que cuenta con un proceso de montaje final del producto que se realiza sobre una cinta transportadora recorriendo sucesivos puestos, y en cada uno de ellos se realizan una o varias operaciones.

1. El posicionamiento inicial y las paradas o arranques de la línea van sumando
muy pequeños desplazamientos de los blocks sobre la cinta transportadora.

2. Ocasionalmente, algún conjunto queda mal posicionado, excediendo el
margen tolerado. Esto afecta algunas operaciones críticas que demandan
alta precisión.

3. En estos casos, el robot es incapaz de montar la pieza y la operación se
interrumpe.

4. La consecuencia es la detención de toda la línea, la necesidad de asistencia
técnica y un tiempo de parada que afecta a toda la actividad de montaje.


Volviendo al problema, ¿cuánta inteligencia es necesaria?
En esta situación problemática, sería la mínima necesaria y suficiente para incorporar a
los robots la capacidad de acomodar su desempeño a la alteración de las distancias en
las trayectorias de las operaciones requeridas.

Otra pregunta a tener en cuenta, ¿por qué incorporar una autonomía o inteligencia
limitada?
Muy simple, la inteligencia en las máquinas tiene un costo, y en casos como este, los
robots solo necesitan superar ciertas dificultades claramente delimitadas. Es decir que
el costo no está linealmente relacionado con el nivel de inteligencia, su crecimiento es
exponencial, por lo que puede llegar a ser muy elevado, absolutamente injustificado e
inabordable



La búsqueda exhaustiva explora sistemáticamente todas las posibles posiciones hasta encontrar la solución. No utiliza conocimiento previo o heurísticas.
Para la implementación de esta búsqueda en el código se realizo la búsqueda en profundidad, recorriendo primero la rama izquierda y luego la rama derecha en busca de la solución.

Ventajas:
Completa: garantiza encontrar la solución si existe.
Sencillez: fácil de implementar y no requiere conocimientos adicionales del problema.

Limitaciones:
Ineficiencia: puede ser muy costosa en términos de tiempo y recursos, ya que evalúa todas las posibles soluciones.
Escalabilidad: en problemas grandes, el espacio de búsqueda puede ser inmanejable.



La búsqueda heurística utiliza una función de evaluación para guiar la búsqueda hacia las posiciones más prometedoras, en lugar de explorar todas las opciones.
Para la implementación se tomo como función Heurística, la distancia entre la posición actual y la posición objetivo.

Ventajas:
Eficiencia: reduce considerablemente el espacio de búsqueda si la heurística está bien diseñada.
Tiempo de resolución: más rápido en comparación con la búsqueda exhaustiva en problemas grandes.

Limitaciones:
Incompleta o no óptima: si la heurística es inadecuada, puede llevar a una solución subóptima o no encontrar una solución.
Diseño de la heurística: requiere conocimiento del problema para definir una función heurística efectiva.


Lo primero fue armar el espacio de estados, lo cual se decidió por hacer un árbol, donde la raíz sea la posición actual del block, esta raíz tendría 2 ramas, una para moverse hacia la izquierda y otra hacia la derecha, luego, los nodos pertenecientes a la rama izquierda tendrían solo hijos izquierdos y los nodos pertenecientes a la rama derecha, tendrían solo hijos derechos, esto es porque si se recorre por la rama izquierda se avanzaía hacia la izquierda y el hecho de explorar un hijo derecho seria retroceder hacia la derecha, lo que sería igual a volver al nodo padre.
La longitud de cada rama seria la longitud total en la que los brazos puedan actuar, donde cada nodo representa una distancia desde la posición inicial del block hasta el nodo, la cual esta medida dependerá de que tan exacto tiene que estar posicionado el block (cm, mm, etc.).
Las rama izquierda está representada por números negativos y la rama derecha está representada por números positivos, porque se toma como punto central al block en su posición actual, lo que si se tiene que mover a una posición objetivo de -3, quiere decir que se tiene que mover el block de su posición actual 3 pasos a la izquierda, y si la posición objetivo fuera 3, seria 3 pasos a la derecha.


##Ejecucion
La ejeucion correcta seria desde el archivo Busquedas_IA.java, ya que allí se muestra el menú de opciones para elegir que busqueda utilizar y donde se establece toda la estructura de datos para resolver el problema.

