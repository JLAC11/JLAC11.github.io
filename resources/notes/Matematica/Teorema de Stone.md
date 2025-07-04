# Teorema de Stone

Debido a este teorema, se tiene por seguro que existe [consistencia](Consistencia%20%28estad%C3%ADstica%29.md) universal para algunos estimadores. Deben cumplirse las siguientes condiciones:

1. Existe $c\in\mathbb{R} | \forall f\ge 0\ \text{y}\ \mathbb{E}(f(x)) < \infty\Rightarrow \mathbb{E}\left[\sum_{i=1}^n\left|W_{ni}(X)\right|f(X_i)\right]\le c \mathbb{E}(f(x))$, o el valor esperado está acotado
1. $\exists \mathcal{D}\ge 1 | \mathbb{P}\left(\sum_{i=1}^n\left|W_{ni}(X)\right|\le \mathcal{D}\right)=1$ Los pesos acotados y la suma converge a 1
1. $\forall a>0$:$$\lim_{n\rightarrow\infty}\mathbb{E}\left[\sum_{i=1}^n\left|W_{ni}(X)\right|\mathbb{1}_{||X_i-X|| > a}\right]=0$$ La estimación en $x$ sólo depende de los puntos cercanos
1. $$\text{Pr}\left(\sum_{i=1}^n W_{ni}(X)\right)\rightarrow 1$$ Los pesos acotados y la suma converge a 1
1. $\lim_{n\rightarrow\infty}\mathbb{E}\left[\sum_{i=1}^nW_{ni}(X)^2\right]=0$ Los pesos tienden a 0.
