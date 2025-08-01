# Operador de Koopman

Si consideramos la *serie de tiempo* $\{\mathbf{x}_n\}$, que puede ser comprendida como un campo espacio-temporal $u(\mathbf{x},n)$ generado de la evolución de un [sistema dinámico](Sistema%20din%C3%A1mico.md) $(\mathcal{M},n,\mathbf{F})$.

Alternativamente, si se considera un tiempo continuo, el sistema dinámico $(\mathcal{M},t,\mathbf{F}^t)$ tiene a $t$ como el tiempo continuo, y el mapeo $\mathbf{F}^t$ evoluciona conforme $\mathbf{x}_0\longmapsto\mathbf{F}^t(\mathbf{x}_0)=\mathbf{x}_t$.
Debido a que es común medir los sistemas dinámicos continuos a intervalos determinados, entonces puede relacionarse el operador del sistema dinámico en tiempo discreto con el continuo al ser muestreado cada $\Delta t$ de tiempo, o alternativamente $\mathbf{F}^{\Delta t}(\mathbf{x}_t)=\mathbf{x}_{t+\Delta t}$.

Entonces, un [operador de Koopman](Operador%20de%20Koopman.md#operador-de-koopman) se define como el *operador*
$\mathcal{K}:\mathcal{F}\mapsto\mathcal{F}$, donde $\mathcal{F}$ son observables o funciones del espacio estado $\phi:\mathcal{M}\rightarrow\mathbb{C}$, donde se define de la siguiente manera:
$$(\mathcal{K}\phi)(x) = \left(\phi\circ\mathbf{F}\right)(x) = \phi\left(\mathbf{F}(x)\right)$$
Debido a que $\mathcal{K}\phi$ es un elemento en el espacio de funciones $\mathcal{F}$, puede definirse como un sistema dinámico $(\mathcal{F},n,\mathcal{K})$, donde $\mathcal{K}$ opera sobre los observables $\phi\in\mathcal{F}$ a una nueva función $\mathcal{K}\phi$ "un paso en el futuro". Debido a que actúa sobre el espacio de funciones $\mathcal{F}$, $\mathcal{K}$ es de dimensión *infinita*, a diferencia de los sistemas dinámicos $\mathbf{F}$ que son de dimensión *finita*. Sin embargo, a diferencia de los sistemas dinámicos tradicionales, el operador de Koopman siempre es lineal, debido a que opera sobre los "observables" del sistema. Estos observables, si se tiene una variable $x$, son por ejemplo $(x^2,x^3,\sin(x),\ln(x),\exp(x),\Gamma(x),...)$, y puede ser una combinación lineal infinita.

Debido a que el operador de Koopman es lineal, entonces se pueden estudiar sus propiedades espectrales, como los *eigenvalores* ($\mu_k$) o las *eigenfunciones* ($\phi_k$). Es muy relevante conocer estos eigenvalores y eigenfunciones porque, aunque probablemente la dimensión de $\mathcal{K}$ probablemente sea infinita, si se toman las eigenfunciones tales que describan al [estado observable completo](../Control/Observabilidad.md) $\mathbf{g(x)=x}$, entonces a pesar de que $\mathcal{K}$ sea infinito, su proyección puede ser finita, donde si se toma un conjunto adecuado de $K$ eigenfunciones $\{\phi_k\}_{k=1}^K$ entonces puede describirse como un conjunto lineal, de la siguiente manera:

$$\textbf{x}=\textbf{g(x)}=\sum_{k=1}^K\xi_k\phi_k(\textbf{x}) $$

Donde $\xi_k$ es el coeficiente de la proyección de la eigenfunción $k$, conocido también como el modo de Koopman correspondiente a la función $\phi_k$, y $\mathbf{g(x)}$ es el estado observable completo, y $\mathbf{g}:\mathcal{M}\mapsto \mathbb{R}^N$, compuesto de cada uno de los valores observables $g_i$, que es una función ($g_i\in\mathcal{F}$). Vale la pena mencionar que existe la posibilidad de que si no se encuentre un conjunto adecuado de $K$ eigenfunciones, que $K$ (y por tanto el número de funciones $\phi_k$) sea infinito.

Los sistemas $(\mathcal{M},n,\mathbf{F})$ y $(\mathcal{F},n,\mathcal{K})$ son dos representaciones distintas de la misma evolución, como se puede ver en la ecuación de arriba, por lo que puede verse la evolución con $\textbf{F}$ o a través del observable $\textbf{g(x)}$ a través del operador de Koopman, de la siguiente manera:
$$\textbf{F(x)}=\mathcal{K}\mathbf{g(x)}=\sum_{k=1}^K\mu_k\xi_k\phi_k$$
Debido a que son exactamente lo mismo, y que los sistemas son *lineales*
