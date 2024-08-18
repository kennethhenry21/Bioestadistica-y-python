# Capítulo 2: Estadística Descriptiva

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
