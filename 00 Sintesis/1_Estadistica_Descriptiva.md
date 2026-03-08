---
marp: true
theme: academic
math: katex
paginate: true
---

<!-- _class: lead -->
# Estadística I
## Síntesis — UNM · FCEQyN · 2025
### Valentino Mende

---

<!-- _class: lead -->
# ¿Qué es la Estadística?

---

# Definición y ramas

La estadística es un conjunto de técnicas que, partiendo de la observación de un fenómeno, permite obtener conclusiones útiles.

| Rama | Función |
|:---|:---|
| **Descriptiva** | Recoger, clasificar, resumir y analizar datos |
| **Inferencial** | Generar predicciones con cierto grado de confianza |

> Las ramas no se oponen — **se complementan**.

---

# Conceptos clave

- **Población (N):** conjunto total de unidades de análisis
- **Muestra (n):** subconjunto representativo de la población
- **Parámetro:** medida numérica que describe la **población**
- **Estadístico / Estimador:** medida numérica que describe la **muestra**

**Variables:**
- *Cuantitativas:* discretas (enteras) o continuas (fraccionarias)
- *Cualitativas:* nominales (sin orden) u ordinales (con orden)

---

<!-- _class: lead -->
# Distribución de Frecuencias

---

# Tabla de frecuencias

Organiza los datos por clases o intervalos para facilitar el análisis.

| Tamaño (KB) | $f_i$ | $F_i$ |
|:---:|:---:|:---:|
| 0 – 100 | 22 | 22 |
| 100 – 200 | 35 | 57 |
| 200 – 300 | 24 | 81 |
| 300 – 400 | 13 | 94 |
| 400 – 500 | 6 | 100 |

- **$f_i$** (absoluta): veces que aparece la modalidad
- **$F_i$** (acumulada): suma progresiva de $f_i$
- **Frecuencia relativa:** $h_i = f_i / N \in [0,1]$

---

# Construcción de intervalos

**Regla de Sturges** → número de clases recomendado:

$$k \approx 1 + 3{,}322 \cdot \log_{10}(n)$$

**Amplitud de clase:**

$$\text{Amplitud} = \frac{\text{Rango}}{k} = \frac{\text{Máx} - \text{Mín}}{k}$$

**Marca de clase:** punto medio del intervalo → usado para cálculos sobre datos agrupados.

---

<!-- _class: lead -->
# Medidas de Tendencia Central

---

# Las tres medidas principales

| Medida | Fórmula | Ventaja | Desventaja |
|:---|:---|:---|:---|
| **Media** | $\bar{x} = \frac{\sum x_i}{n}$ | Usa todos los datos | Sensible a extremos |
| **Mediana** | valor central ordenado | Robusta a extremos | No usa todos los datos |
| **Moda** | valor más frecuente | Funciona con cualitativos | Puede no existir |

En distribución **simétrica:** $\text{Media} = \text{Mediana} = \text{Moda}$

En distribución **asimétrica:** difieren entre sí.

---

# Media para datos agrupados

$$\bar{x} = \frac{\sum f_i \cdot x_i}{n}$$

donde $x_i$ es la **marca de clase** y $f_i$ la frecuencia de cada intervalo.

---

<!-- _class: lead -->
# Medidas de Posición

---

# Cuartiles, Deciles y Percentiles

Dividen los datos ordenados en partes iguales para **ubicar un dato respecto al resto**.

| Medida | Divisiones | Referencia |
|:---|:---:|:---|
| **Cuartiles** $Q_1, Q_2, Q_3$ | 4 | $Q_2$ = Mediana |
| **Deciles** $D_1 \ldots D_9$ | 10 | $D_5$ = Mediana |
| **Percentiles** $P_1 \ldots P_{99}$ | 100 | $P_{50}$ = Mediana |

> *Ejemplo:* estar en el **percentil 80** significa superar al 80% de la muestra.

---

# Rango Intercuartílico y Outliers

$$IQR = Q_3 - Q_1$$

Mide la dispersión del **50% central**, robusto frente a valores extremos.

**Criterio de valores atípicos:**

$$x < Q_1 - 1{,}5 \cdot IQR \quad \text{o} \quad x > Q_3 + 1{,}5 \cdot IQR$$

El **boxplot** representa visualmente $Q_1$, $Q_2$, $Q_3$, mínimos, máximos y outliers.

---

<!-- _class: lead -->
# Medidas de Dispersión

---

# ¿Por qué medir la dispersión?

Dos conjuntos pueden tener la **misma media** pero diferir en cómo se distribuyen sus datos.

| Medida | Fórmula | Observación |
|:---|:---|:---|
| **Rango** | Máx $-$ Mín | Simple, sensible a extremos |
| **Varianza** | $s^2 = \frac{\sum(x_i-\bar{x})^2}{n-1}$ | Eleva desviaciones al cuadrado |
| **Desv. estándar** | $s = \sqrt{s^2}$ | Mismas unidades que la variable |
| **Coef. variación** | $CV = \frac{s}{\bar{x}} \cdot 100$ | Permite comparar distribuciones |

---

# Distribución Normal — Regla Empírica

Cuando la distribución es **aproximadamente normal**:

$$68\% \text{ de datos en } \bar{x} \pm 1s$$
$$95\% \text{ de datos en } \bar{x} \pm 2s$$
$$99{,}7\% \text{ de datos en } \bar{x} \pm 3s$$

Con solo **media** y **desviación estándar** queda completamente determinada.

---

<!-- _class: lead -->
# Asimetría y Curtosis

---

# Asimetría

Mide el **grado de simetría** de una distribución.

$$g_1 = \frac{\frac{1}{n}\sum(x_i - \bar{x})^3}{s^3}$$

| Valor | Interpretación |
|:---:|:---|
| $g_1 = 0$ | Distribución simétrica |
| $g_1 > 0$ | Sesgo hacia la derecha (cola larga a la derecha) |
| $g_1 < 0$ | Sesgo hacia la izquierda (cola larga a la izquierda) |

> Se eleva al **cubo** para conservar el signo y dar mayor peso a valores extremos.

---

# Curtosis

Mide el **grado de concentración** de los datos alrededor de la media.

$$g_2 = \frac{\frac{1}{n}\sum(x_i - \bar{x})^4}{s^4}$$

| Tipo | Exceso ($g_2 - 3$) | Forma |
|:---|:---:|:---|
| Mesocúrtica | $= 0$ | Similar a la normal |
| Leptocúrtica | $> 0$ | Más picuda, colas pesadas |
| Platicúrtica | $< 0$ | Más achatada, colas livianas |

> La distribución **normal** tiene curtosis $= 3$ y sirve como referencia.

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **Distribución de frecuencias** | Organizar y tabular datos |
| **Tendencia central** | Encontrar el "corazón" de los datos |
| **Dispersión** | Medir la variabilidad |
| **Posición** | Ubicar datos dentro de la distribución |
| **Forma** | Describir simetría y concentración |

---

# Idea final

La estadística descriptiva **no busca predecir ni validar hipótesis**.

Su objetivo es **comprender y comunicar claramente** la información contenida en los datos.

> *"En Dios confiamos, todos los demás deben traer datos."*
> — W. Edwards Deming

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
