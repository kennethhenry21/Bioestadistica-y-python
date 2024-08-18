# Capítulo 3: Probabilidad y Distribuciones de Probabilidad

**3.1. Teoría de la Probabilidad**

La probabilidad es la rama de las matemáticas que estudia la incertidumbre y permite cuantificar la posibilidad de que un evento ocurra.

* **Espacio Muestral (S)**: Conjunto de todos los resultados posibles de un experimento. Ejemplo: Lanzar una moneda, S = {cara, cruz}.
* **Evento (E)**: Cualquier subconjunto del espacio muestral. Ejemplo: Obtener cara al lanzar una moneda.
* **Probabilidad de un Evento**: Se define como el cociente entre el número de resultados favorables al evento y el número total de resultados posibles, si todos los resultados son igualmente probables.

**3.2. Ejemplo en Python: Simulación de Eventos Probabilísticos**

**Objetivo**: Simular el lanzamiento de una moneda 10,000 veces y calcular la probabilidad de obtener cara.

```python
import numpy as np

# Simulando el lanzamiento de una moneda 10,000 veces
np.random.seed(42)
lanzamientos = np.random.choice(['cara', 'cruz'], size=10000, replace=True)

# Calculando la probabilidad de obtener cara
caras = np.sum(lanzamientos == 'cara')
probabilidad_cara = caras / len(lanzamientos)

print(f"Probabilidad de obtener cara: {probabilidad_cara:.4f}")

```

```
Probabilidad de obtener cara: 0.5013
```

**Explicación**:

* Se realiza una simulación de 10,000 lanzamientos de una moneda justa.
* Se calcula la probabilidad empírica de obtener cara.

**3.3. Distribuciones de Probabilidad**

Una distribución de probabilidad describe cómo se distribuyen los valores de una variable aleatoria. Existen diferentes tipos de distribuciones, cada una con sus propias propiedades y aplicaciones.

* **Distribución Normal**: Es una de las distribuciones más importantes en estadística. Es simétrica y tiene forma de campana. La media, mediana y moda son iguales.
* **Distribución Binomial**: Describe el número de éxitos en una secuencia de ensayos independientes de tipo éxito/fracaso.
* **Distribución de Poisson**: Modelo que se utiliza para contar el número de eventos que ocurren en un intervalo de tiempo o espacio.

**3.4. Ejemplo en Python: Visualización de Distribuciones**

**Objetivo**: Visualizar las distribuciones normal, binomial y de Poisson.

```python
import numpy as np
import matplotlib.pyplot as plt
import scipy.stats as stats

# Configuración de la figura
plt.figure(figsize=(12, 6))

# Distribución Normal
x_norm = np.linspace(-3, 3, 1000)
y_norm = stats.norm.pdf(x_norm)
plt.plot(x_norm, y_norm, label='Distribución Normal', color='blue')

# Distribución Binomial
n, p = 10, 0.5  # Número de ensayos y probabilidad de éxito
x_binom = np.arange(0, n+1)
y_binom = stats.binom.pmf(x_binom, n, p)
plt.vlines(x_binom, 0, y_binom, label='Distribución Binomial', colors='green', lw=5, alpha=0.5)

# Distribución de Poisson
mu = 3  # Tasa de ocurrencia
x_poisson = np.arange(0, 15)
y_poisson = stats.poisson.pmf(x_poisson, mu)
plt.vlines(x_poisson, 0, y_poisson, label='Distribución de Poisson', colors='red', lw=5, alpha=0.5)

# Configuración de la gráfica
plt.title('Visualización de Distribuciones de Probabilidad')
plt.xlabel('Valores')
plt.ylabel('Probabilidad')
plt.legend()
plt.show()

```

<figure><img src=".gitbook/assets/Captura desde 2024-08-18 00-04-45.png" alt=""><figcaption></figcaption></figure>

**Explicación**:

* Se generan y visualizan tres tipos diferentes de distribuciones de probabilidad: normal, binomial y de Poisson.
* La distribución normal se presenta como una curva suave, mientras que las distribuciones binomial y de Poisson son discretas.
