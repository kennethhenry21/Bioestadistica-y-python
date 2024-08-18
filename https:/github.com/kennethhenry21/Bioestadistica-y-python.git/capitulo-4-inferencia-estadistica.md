# Capítulo 4: Inferencia Estadística

**4.1. Intervalos de Confianza**

Un intervalo de confianza es un rango de valores, calculado a partir de los datos de la muestra, que se utiliza para estimar un parámetro desconocido de la población con un cierto nivel de confianza.

* **Interpretación**: Si calculamos muchos intervalos de confianza de 95% en diferentes muestras, esperamos que el 95% de ellos contengan la media verdadera de la población.
* **Cálculo**: Se utiliza la media de la muestra, el valor crítico de la distribución y la desviación estándar.

**4.2. Ejemplo en Python: Cálculo de Intervalos de Confianza**

**Objetivo**: Calcular un intervalo de confianza del 95% para la media de una muestra.

```python
import numpy as np
import scipy.stats as stats

# Simulando un conjunto de datos
np.random.seed(42)
muestra = np.random.normal(70, 10, 100)

# Cálculo del intervalo de confianza del 95%
media_muestra = np.mean(muestra)
sem = stats.sem(muestra)  # Error estándar de la media
intervalo = stats.t.interval(0.95, len(muestra)-1, loc=media_muestra, scale=sem)

print(f"Intervalo de confianza del 95%: {intervalo}")

```

```
Intervalo de confianza del 95%: (67.15953163638099, 70.76353801573714)
```

**Explicación**:

* Se simula una muestra de datos y se calcula un intervalo de confianza del 95% para la media.
* El intervalo de confianza nos da un rango dentro del cual esperamos que se encuentre la media verdadera de la población.

**4.3. Pruebas de Hipótesis**

Una prueba de hipótesis es un procedimiento estadístico que se utiliza para tomar decisiones sobre la verdad de una hipótesis estadística.

* **Hipótesis Nula (H₀)**: Afirmación que se asume verdadera hasta que se demuestre lo contrario. Ejemplo: "La media de la población es igual a 70."
* **Hipótesis Alternativa (H₁)**: Afirmación que se acepta si la evidencia proporciona suficiente soporte para rechazar H₀. Ejemplo: "La media de la población es diferente de 70."
* **Pruebas t y z**: Se utilizan para comparar la media de una muestra con la media de una población conocida o para comparar dos medias muestrales.

**4.4. Ejemplo en Python: Realización de Pruebas de Hipótesis**

**Objetivo**: Realizar una prueba t para comparar la media de una muestra con un valor hipotético.

```python
import numpy as np
import scipy.stats as stats

# Simulando un conjunto de datos
np.random.seed(42)
muestra = np.random.normal(70, 10, 30)

# Hipótesis nula: La media es 70
media_hipotetica = 70

# Prueba t de una muestra
t_stat, p_value = stats.ttest_1samp(muestra, media_hipotetica)

print(f"Estadístico t: {t_stat:.4f}")
print(f"Valor p: {p_value:.4f}")

if p_value < 0.05:
    print("Rechazamos la hipótesis nula.")
else:
    print("No podemos rechazar la hipótesis nula.")

```

```
Estadístico t: -1.1450
Valor p: 0.2616
No podemos rechazar la hipótesis nula.
```

**Explicación**:

* Se simula una muestra de datos y se realiza una prueba t para determinar si la media de la muestra es significativamente diferente de un valor hipotético.
* El resultado de la prueba t se interpreta utilizando el valor p, comparado con un nivel de significancia (por lo general 0.05).
