# Capítulo 5: Correlación y Regresión

**5.1. Coeficiente de Correlación**

El coeficiente de correlación mide la fuerza y la dirección de la relación lineal entre dos variables. Es un valor entre -1 y 1.

* **Coeficiente de Correlación de Pearson**: Es el más común y mide la relación lineal entre dos variables continuas.
  * **Interpretación**:
    * 1: Correlación positiva perfecta.
    * 0: No hay correlación.
    * \-1: Correlación negativa perfecta.

**5.2. Ejemplo en Python: Cálculo del Coeficiente de Correlación**

**Objetivo**: Calcular el coeficiente de correlación entre dos variables simuladas.

```python
import numpy as np
import matplotlib.pyplot as plt

# Simulando dos variables
np.random.seed(42)
x = np.random.rand(100) * 10  # Variable independiente
y = 2 * x + np.random.normal(0, 2, 100)  # Variable dependiente con algo de ruido

# Cálculo del coeficiente de correlación de Pearson
correlacion = np.corrcoef(x, y)[0, 1]

print(f"Coeficiente de correlación de Pearson: {correlacion:.4f}")

# Visualización de la relación entre las variables
plt.scatter(x, y)
plt.title('Relación entre X e Y')
plt.xlabel('X')
plt.ylabel('Y')
plt.show()
```

```
Coeficiente de correlación de Pearson: 0.9530
```

<figure><img src=".gitbook/assets/Captura desde 2024-08-18 00-08-23.png" alt=""><figcaption></figcaption></figure>

**Explicación**:

* Se simulan dos variables: una independiente y una dependiente con una relación lineal.
* Se calcula el coeficiente de correlación de Pearson y se visualiza la relación entre las variables.

**5.3. Regresión Lineal Simple**

La regresión lineal es un método estadístico que permite modelar la relación entre una variable dependiente y una o más variables independientes.

* **Modelo de Regresión Lineal Simple**: Se expresa como Y=β0+β1X+ϵY = \beta\_0 + \beta\_1X + \epsilonY=β0​+β1​X+ϵ, donde:
  * YYY es la variable dependiente.
  * XXX es la variable independiente.
  * β0\beta\_0β0​ es la ordenada al origen (intercepto).
  * β1\beta\_1β1​ es la pendiente del modelo (coeficiente de regresión).
  * ϵ\epsilonϵ es el término de error.

**5.4. Ejemplo en Python: Ajuste de un Modelo de Regresión Lineal**

**Objetivo**: Ajustar un modelo de regresión lineal a un conjunto de datos y analizar los resultados.

```python
from sklearn.linear_model import LinearRegression
import numpy as np
import matplotlib.pyplot as plt

# Simulando datos
np.random.seed(42)
x = np.random.rand(100).reshape(-1, 1) * 10  # Variable independiente
y = 2 * x + np.random.normal(0, 2, 100).reshape(-1, 1)  # Variable dependiente

# Ajuste del modelo de regresión lineal
modelo = LinearRegression()
modelo.fit(x, y)

# Predicciones del modelo
y_pred = modelo.predict(x)

# Parámetros del modelo
intercepto = modelo.intercept_[0]
pendiente = modelo.coef_[0][0]

print(f"Intercepto: {intercepto:.4f}")
print(f"Pendiente: {pendiente:.4f}")

# Visualización del ajuste
plt.scatter(x, y, label='Datos')
plt.plot(x, y_pred, color='red', label='Modelo ajustado')
plt.title('Regresión Lineal Simple')
plt.xlabel('X')
plt.ylabel('Y')
plt.legend()
plt.show()

```

```
Intercepto: 0.4302
Pendiente: 1.9080
```

<figure><img src=".gitbook/assets/Captura desde 2024-08-18 00-17-51.png" alt=""><figcaption></figcaption></figure>

**Explicación**:

* Se ajusta un modelo de regresión lineal simple utilizando `sklearn`.
* Se visualiza el modelo ajustado junto con los datos originales para analizar cómo se ajusta la línea de regresión.
