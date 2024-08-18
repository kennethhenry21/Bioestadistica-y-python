# Capítulo 1: Introducción a la Estadística

1.1. Conceptos Básicos

La estadística es una rama de las matemáticas que se ocupa de la recopilación, análisis, interpretación, y presentación de datos. En ciencias biológicas y de la salud, la estadística es fundamental para diseñar experimentos, analizar datos, y sacar conclusiones.

* **Población**: Conjunto completo de individuos o elementos que son objeto de estudio. Ejemplo: Todos los pacientes de un hospital.
* **Muestra**: Subconjunto de la población que se selecciona para el estudio. Ejemplo: 100 pacientes seleccionados aleatoriamente de un hospital.
* **Muestra Representativa**: Una muestra que refleja las características esenciales de la población.

**1.2. Tipos de Muestreo**

* **Muestreo Aleatorio Simple**: Cada individuo de la población tiene la misma probabilidad de ser seleccionado.
* **Muestreo Estratificado**: La población se divide en grupos (estratos) y se toma una muestra aleatoria de cada estrato.
* **Muestreo en Conglomerados**: Se divide la población en conglomerados (grupos) y se selecciona aleatoriamente un número de conglomerados para estudiar.

**1.3. Ejemplo en Python**

**Objetivo**: Generar una muestra aleatoria de una población utilizando `numpy` y analizar su representatividad.

{% code overflow="wrap" %}
```python
import numpy as np
import matplotlib.pyplot as plt

# Simulando una población de 10,000 individuos con edades entre 18 y 80 años
np.random.seed(42)
poblacion = np.random.randint(18, 80, 10000)

# Muestreo aleatorio simple: Tomamos una muestra de 100 individuos
muestra = np.random.choice(poblacion, 100, replace=False)

# Visualizando la distribución de la población y la muestra
plt.figure(figsize=(10, 5))
plt.hist(poblacion, bins=30, alpha=0.5, label='Población')
plt.hist(muestra, bins=30, alpha=0.5, label='Muestra')
plt.legend(loc='upper right')
plt.title('Distribución de edades en la población y la muestra')
plt.xlabel('Edad')
plt.ylabel('Frecuencia')
plt.show()

```
{% endcode %}

<figure><img src=".gitbook/assets/Captura desde 2024-08-17 23-59-00.png" alt=""><figcaption></figcaption></figure>

**Explicación**:

* Se simula una población de 10,000 individuos con edades entre 18 y 80 años.
* Se selecciona una muestra aleatoria de 100 individuos.
* Se visualizan las distribuciones de edades en la población y en la muestra, permitiendo evaluar si la muestra es representativa.

#### **Capítulo 2: Estadística Descriptiva**

**2.1. Medidas de Tendencia Central**

* **Media (Promedio)**: Suma de todos los valores dividida por el número total de valores.
* **Mediana**: Valor que divide los datos ordenados en dos partes iguales.
* **Moda**: Valor que aparece con más frecuencia en un conjunto de datos.

**2.2. Medidas de Dispersión**

* **Rango**: Diferencia entre el valor máximo y mínimo.
* **Varianza**: Medida que indica qué tan dispersos están los datos respecto a la media.
* **Desviación Estándar**: Raíz cuadrada de la varianza, indicando la dispersión promedio de los datos.

**2.3. Ejemplo en Python**

**Objetivo**: Calcular las medidas de tendencia central y dispersión para un conjunto de datos biológicos.

```python
import numpy as np

# Simulando un conjunto de datos: Pesos de 100 individuos en kg
np.random.seed(42)
pesos = np.random.normal(70, 10, 100)

# Calculando medidas de tendencia central
media = np.mean(pesos)
mediana = np.median(pesos)
moda = np.argmax(np.bincount(pesos.astype(int)))

# Calculando medidas de dispersión
rango = np.ptp(pesos)
varianza = np.var(pesos)
desviacion_estandar = np.std(pesos)

print(f"Media: {media:.2f} kg")
print(f"Mediana: {mediana:.2f} kg")
print(f"Moda: {moda} kg")
print(f"Rango: {rango:.2f} kg")
print(f"Varianza: {varianza:.2f} kg^2")
print(f"Desviación Estándar: {desviacion_estandar:.2f} kg")

```

```
Media: 68.96 kg
Mediana: 68.73 kg
Moda: 73 kg
Rango: 44.72 kg
Varianza: 81.65 kg^2
Desviación Estándar: 9.04 kg
```

**Explicación**:

* Se simulan los pesos de 100 individuos usando una distribución normal.
* Se calculan la media, mediana, moda, rango, varianza y desviación estándar de los pesos.
