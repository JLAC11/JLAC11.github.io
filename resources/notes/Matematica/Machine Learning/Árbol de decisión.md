# Árbol de decisión

Un árbol de decisión es una técnica de [clasificación](Clasificaci%C3%B3n.md) donde se toman decisiones, normalmente como un *árbol binario* donde cada nodo con hijos toma una decisión, y en las hojas del árbol se encuentra el resultado.

````python
from sklearn.tree import DecisionTreeClassifier
# Asumiendo que ya se tienen tanto la variable objetivo 
# como los otros datos
model = DecisionTreeClassifier(random_state=42)
model.fit(X_train, Y_train)
print(classification_report(y_test,y_pred))# REVISAR

````

![Pasted image 20220511212133.png](../../Images/Pasted%20image%2020220511212133.png)
Y_i es el dato, Y_a es el promedio dentro de la celda A
