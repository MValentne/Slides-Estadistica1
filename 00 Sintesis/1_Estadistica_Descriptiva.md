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
# Estadística Descriptiva
## Organizar, resumir y comunicar datos

---

# Contexto: ¿qué es la estadística?

| Rama | Función |
|:---|:---|
| **Descriptiva** | Recoger, clasificar, resumir y analizar datos |
| **Inferencial** | Generar predicciones con cierto grado de confianza |

| Concepto | Definición |
|:---|:---|
| **Población (N)** / **Muestra (n)** | Conjunto total / subconjunto representativo |
| **Parámetro** / **Estadístico** | Medida de la población / de la muestra |
| **Variable cuantitativa** | Discreta (contada) o continua (medida) |
| **Variable cualitativa** | Nominal (sin orden) u ordinal (con orden) |

> Esta unidad se ocupa exclusivamente de **describir** — sin predecir ni validar.

---

<!-- _class: lead -->
# Distribución de Frecuencias
## El primer paso: organizar los datos

---

# Tabla de frecuencias

Organiza los datos por clases o intervalos para facilitar el análisis.

| Tamaño (KB) | $f_i$ | $F_i$ | $h_i$ |
|:---:|:---:|:---:|:---:|
| 0 – 100 | 22 | 22 | 0,22 |
| 100 – 200 | 35 | 57 | 0,35 |
| 200 – 300 | 24 | 81 | 0,24 |
| 300 – 400 | 13 | 94 | 0,13 |
| 400 – 500 | 6 | 100 | 0,06 |

- **$f_i$** (absoluta): veces que aparece la modalidad
- **$F_i$** (acumulada): suma progresiva de $f_i$
- **$h_i$** (relativa): $f_i / N \in [0,1]$

---

# Construcción de intervalos

**Regla de Sturges** → número de clases recomendado:

$$k \approx 1 + 3{,}322 \cdot \log_{10}(n)$$

**Amplitud de clase:**

$$\text{Amplitud} = \frac{\text{Rango}}{k} = \frac{\text{Máx} - \text{Mín}}{k}$$

**Marca de clase:** punto medio del intervalo, usada para calcular la media sobre datos agrupados:

$$\bar{x} = \frac{\sum f_i \cdot x_i}{n}$$

---

<!-- _class: lead -->
# Medidas de Tendencia Central
## ¿Dónde está el "centro" de los datos?

---

# Las tres medidas principales

| Medida | Fórmula | Ventaja | Desventaja |
|:---|:---|:---|:---|
| **Media** | $\bar{x} = \frac{\sum x_i}{n}$ | Usa todos los datos | Sensible a extremos |
| **Mediana** | valor central ordenado | Robusta a extremos | No usa todos los datos |
| **Moda** | valor más frecuente | Funciona con cualitativos | Puede no existir |

En distribución **simétrica:** Media $=$ Mediana $=$ Moda

En distribución **asimétrica:** difieren — y esa diferencia es informativa.

---

# Ejemplo: efecto de un valor extremo

Salarios mensuales (en miles): **22, 24, 25, 26, 26, 27, 28, 150**

$$\bar{x} = \frac{22+24+25+26+26+27+28+150}{8} = \mathbf{41{,}0}$$

$$\text{Mediana} = \frac{26+26}{2} = \mathbf{26{,}0} \qquad \text{Moda} = \mathbf{26}$$

El valor extremo (150) arrastra la media hacia arriba — **ningún empleado gana cerca de 41**.

> En distribuciones asimétricas, la **mediana** representa mejor al grupo que la media.

---

<!-- _class: lead -->
# Medidas de Posición
## Ubicar un dato dentro de la distribución

---

# Cuartiles, Deciles y Percentiles

Dividen los datos ordenados en partes iguales.

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

El **boxplot** representa visualmente $Q_1$, $Q_2$, $Q_3$, mínimos, máximos y outliers en una sola figura.

---

<!-- _class: lead -->
# Medidas de Dispersión
## ¿Qué tan variables son los datos?

---

# Las medidas de dispersión

| Medida | Fórmula | Observación |
|:---|:---|:---|
| **Rango** | Máx $-$ Mín | Simple, muy sensible a extremos |
| **Varianza** | $s^2 = \frac{\sum(x_i-\bar{x})^2}{n-1}$ | Penaliza desviaciones grandes |
| **Desv. estándar** | $s = \sqrt{s^2}$ | Mismas unidades que la variable |
| **Coef. variación** | $CV = \frac{s}{\bar{x}} \cdot 100$ | Permite comparar distribuciones distintas |

---

# Ejemplo: la media sola no alcanza

Dos sistemas con tiempos de respuesta (ms):

$$A = \{48, 50, 50, 52\} \qquad B = \{10, 30, 70, 90\}$$

$$\bar{x}_A = \bar{x}_B = 50 \text{ ms}$$

$$s_A \approx 1{,}6 \text{ ms} \qquad s_B \approx 34{,}2 \text{ ms}$$

> **Misma media, variabilidad completamente distinta.** El sistema B es impredecible — algo que la media oculta por completo.

El CV permite comparar dispersiones entre variables con distintas escalas o unidades.

---

<!-- _class: lead -->
# Medidas de Forma
## Asimetría y Curtosis

---

# Asimetría

Mide el **grado de simetría** de una distribución.

$$g_1 = \frac{\frac{1}{n}\sum(x_i - \bar{x})^3}{s^3}$$

| Valor | Interpretación |
|:---:|:---|
| $g_1 = 0$ | Distribución simétrica |
| $g_1 > 0$ | Sesgo hacia la derecha — cola larga a la derecha |
| $g_1 < 0$ | Sesgo hacia la izquierda — cola larga a la izquierda |

> Se eleva al **cubo** para conservar el signo y amplificar los valores extremos.

---

# Curtosis

Mide el **grado de concentración** de los datos alrededor de la media.

$$g_2 = \frac{\frac{1}{n}\sum(x_i - \bar{x})^4}{s^4}$$

| Tipo | Exceso ($g_2 - 3$) | Forma |
|:---|:---:|:---|
| Mesocúrtica | $= 0$ | Similar a la normal |
| Leptocúrtica | $> 0$ | Más picuda, colas pesadas |
| Platicúrtica | $< 0$ | Más achatada, colas livianas |

> La distribución **normal** tiene curtosis $= 3$ y sirve como referencia universal.

---

# Regla Empírica

Cuando la distribución es aproximadamente normal, la desviación estándar delimita zonas precisas:

$$68\% \text{ en } \bar{x} \pm 1s \qquad 95\% \text{ en } \bar{x} \pm 2s \qquad 99{,}7\% \text{ en } \bar{x} \pm 3s$$

Con solo **media** y **desviación estándar** la distribución queda completamente determinada.

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Herramienta | Para qué sirve |
|:---|:---|
| **Distribución de frecuencias** | Organizar y tabular los datos |
| **Tendencia central** | Encontrar el "corazón" de los datos |
| **Posición** | Ubicar un dato dentro de la distribución |
| **Dispersión** | Medir la variabilidad |
| **Forma** | Describir simetría y concentración |

La estadística descriptiva **no busca predecir ni validar hipótesis** — busca **comprender y comunicar** la información contenida en los datos.

> *"En Dios confiamos, todos los demás deben traer datos."*
> — W. Edwards Deming

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
