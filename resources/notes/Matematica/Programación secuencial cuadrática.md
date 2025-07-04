# Programación secuencial cuadrática

El problema de [optimización](Optimizaci%C3%B3n.md) estándar a resolver es el siguiente:

$$\begin{align}
\min_{\bar{d}}&\ f(x) \\
\text{s.t.} &\  g(x)\le0 \\
	 &\ h(x)=0
\end{align}$$

Se define el [lagrangiano](../Funci%C3%B3n%20Lagrangiana.md) asociado al problema de la manera siguiente:
$$L(x,u,v) = f(x) +g(x)'u+h(x)'v$$
Donde la comilla representa que se encuentra el vector de funciones transpuesto. Se construye el subproblema QP para cada iteración $k$, linealizando las restricciones alrededor del punto $x_k$ de la siguiente manera:
$$\begin{align}
\min_{d_x}&\ \nabla f(x_k)'d_x+\frac{1}{2} d_xB_kd_x'\\
\text{s.t.} &\  \nabla g(x)d_x+g(x_k)\le0 \\
	 &\ \nabla h(x)d_x + h(x_k)=0
\end{align}$$
Donde $d_x=x-x_k$.D
