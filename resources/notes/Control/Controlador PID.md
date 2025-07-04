# Controlador PID

Un controlador PID es un tipo de [controlador](Control.md) que tiene una parte proporcional, una integral y una derivativa. Se puede describir de la siguiente manera:

$$PID = K_ce(t) + K_I\int_{t_0}^te(t)\mathrm{dt}+K_D\frac{d}{dt}e(t)$$

Cuando se realiza la [transformada de Laplace](../Matematica/Transformada%20de%20Laplace.md), se obtiene la siguiente forma:
$$PID(s) = K_C + \frac{K_I}{s}+K_Ds$$

Es particularmente útil cuando se intenta hacer [Control a lazo cerrado](Control%20a%20lazo%20cerrado.md). Se espera que pueda ser relativamente [robusto](Robustez.md), pues no necesariamente se conoce con certeza el sistema que se desea controlar.
