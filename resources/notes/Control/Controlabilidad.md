# Controlabilidad

La controlabilidad es una medida en la cual un [sistema dinámico](../Dinamica/Sistema%20din%C3%A1mico.md) puede llegar a ser controlado por medio de una acción sobre él. Juega un rol crucial en muchos problemas de [control](Control.md), como la estabilización de sistemas inestables por medio de [control a lazo cerrado](Control%20a%20lazo%20cerrado.md) o *control óptimo*.

## Matriz de controlabilidad

En un *sistema lineal invariante en el tiempo*, descrito en su forma de [espacio estado](../Dinamica/Espacio%20estado.md), se puede calcular la matriz de controlabilidad de la siguiente manera:
$$\mathcal{C} = \left[\matrix{B&AB&A^2B&\dots &A^{n-1}B}\right]$$
El rango de la matriz $\mathcal{C}$ es el rango controlable del espacio estado; si el rango de la matriz es igual al número de estados $n$ que tiene el sistema, entonces se dice que el sistema es controlable.
$$\mathrm{rank}(\mathcal{O}) = n\Rightarrow\mathrm{Observable}$$

Si el rango de la matriz es menor, implica que existen estados no controlables, y la medida de los no controlables es el *kernel* de la matriz.

Es el dual matemático de la [matriz de observabilidad](Observabilidad.md).
