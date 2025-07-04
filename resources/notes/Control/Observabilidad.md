# Observabilidad

La observabilidad de un [sistema dinámico](../Dinamica/Sistema%20din%C3%A1mico.md) es una medida de qué tan bien se pueden inferir los estados de un sistema, con la información provista por las salidas externas.

## Matriz de observabilidad

En un sistema lineal, descrito en su forma de [espacio estado](../Dinamica/Espacio%20estado.md), se puede calcular la matriz de observabilidad de la siguiente manera:
$$\mathcal{O} = \left[\matrix{C\\CA\\CA^2\\\vdots\\CA^{n-1}}\right]$$
El rango de renglón de la matriz $\mathcal{O}$ es el rango observable del espacio estado; si el rango de la matriz es igual al número de estados $n$ que tiene el sistema, entonces se dice que el sistema es observable.
$$\mathrm{rank}(\mathcal{O}) = n\Rightarrow\mathrm{Observable}$$

Si el rango de la matriz es menor, implica que existen estados no observables, y la medida de los no observables es el *kernel* de la matriz.

La matriz de observabilidad es el dual de la matriz de [controlabilidad](Controlabilidad.md).
