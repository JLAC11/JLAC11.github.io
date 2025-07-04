# Función de transferencia

Sea un *sistema lineal invariante en el tiempo* con entradas $X(t)$ y salidas $Y(t)$, entonces, su función de transferencia es definida de la siguiente manera:

$$H(s) = \frac{Y(s)}{X(s)}$$
Donde $H(s)$ es la función de transferencia, y $Y(s)$ y $X(s)$ son las [transformadas de Laplace](../Matematica/Transformada%20de%20Laplace.md) de las salidas y las entradas, respectivamente.

Para una representación de un [espacio estado](Espacio%20estado.md) de un sistema *lineal invariante en el tiempo*:
$$\mathbf{H}(s)=C\left(Is-A\right)^{-1}B+D$$

$$\dot{x} = Ax$$
Anotando la transformada de Laplace:
$$sX(s) = AX(s)$$
Resolviendo la ecuación:
$$sX(s)-AX(s) = 0$$
$$\left(sI-A\right)X(s)=0$$
Puede observarse que la solución de esta ecuación es equivalente a encontrar los *eigenvalores* de la matriz $A$. Estos a su vez representan los *polos* de la función de transferencia.
