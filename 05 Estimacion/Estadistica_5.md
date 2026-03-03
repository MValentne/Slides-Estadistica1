---
marp: true
theme: academic
math: katex
paginate: true
---
# Estadística I
# UNM - FCEQyN - 2025
## Valentino Mende
---
<!-- _class: lead -->
# 05
# Estimación de la Media Poblacional
## Del dato muestral al conocimiento poblacional.
---
En la unidad anterior aprendimos que las medias muestrales se distribuyen normalmente gracias al **Teorema del Límite Central**.

Ahora queremos usar eso para algo concreto: **estimar la media de una población entera** a partir de una sola muestra.

* ¿Cómo resumimos lo que sabemos en un único número?
* ¿Podemos construir un rango con garantía matemática?
* ¿Qué hacemos cuando la muestra es pequeña?

---
<!-- _class: lead -->
# 01
# Estimaciones Puntuales
## Un número para resumir todo.
---
# ¿Qué es una Estimación Puntual?

Una **estimación puntual** es un único valor que se usa para estimar un parámetro de la población.

Los estimadores puntuales más comunes son:

$$\mu \approx \bar{x} \qquad \sigma \approx s \qquad P \approx \hat{p}$$

En esta unidad nos concentramos en estimar la **media poblacional** $\mu$ a partir de la media muestral $\bar{x}$.

---
# El límite de la estimación puntual

La estimación puntual es simple y directa. Pero tiene una limitación fundamental: **no dice nada sobre su propia precisión**.

Si tomamos una muestra y calculamos $\bar{x} = 25.2$, eso no nos dice si $\mu$ está cerca o lejos de ese valor.

* ¿Está a 0.1 de distancia? ¿A 5? ¿A 20?
* La estimación puntual sola **no puede responder eso**.

Para eso necesitamos un enfoque distinto: el intervalo de confianza.

---
<!-- _class: lead -->
# 02
# Estimaciones de Intervalo
## Un rango con garantía matemática.
---
# ¿Qué es un Intervalo de Confianza?

Una **estimación de intervalo** establece la amplitud en la que quizá se encuentre un parámetro poblacional.

El intervalo dentro del cual se espera que esté el parámetro se llama **intervalo de confianza (IC)**.

$$\boxed{IC(1-\alpha) = \bar{x} \pm Z \cdot \frac{s}{\sqrt{n}}}$$

Los dos niveles de confianza más utilizados son **95%** y **99%**.

* Cuando $\sigma$ (desvío poblacional) es conocido, se usa $\sigma$ en lugar de $s$.

---
# Interpretación correcta del IC

Un **IC del 95%** significa que cerca del 95% de todos los intervalos construidos de esta manera contendrán al verdadero parámetro $\mu$.

Equivalentemente: el 95% de las medias muestrales para un tamaño de muestra dado estará dentro de **1.96 desvíos estándar** de la media poblacional.

Para el **IC del 99%**: el 99% de las medias muestrales estará dentro de **2.58 desvíos estándar** de la media poblacional.

* No decimos que $\mu$ tiene 95% de probabilidad de estar en ese intervalo. Es una afirmación sobre el **procedimiento**, no sobre un resultado particular.

---
<!-- _class: lead -->
# Demostración del IC para $\mu$
## ¿De dónde sale la fórmula?
---
# Punto de partida

Por el TLC, para $n \geq 30$, el 95% de las medias muestrales no se aleja más de 2 desvíos de $\mu$:

$$P\!\left(\mu - 2\cdot\frac{\sigma}{\sqrt{n}} < \bar{x} < \mu + 2\cdot\frac{\sigma}{\sqrt{n}}\right) \approx 0.95$$

Aplicamos $-\mu - \bar{x}$ en cada término para **cancelar** $\mu$ del centro y aislar $-\mu$:

$$P\!\left(-2\cdot\frac{\sigma}{\sqrt{n}} - \bar{x} < -\mu < 2\cdot\frac{\sigma}{\sqrt{n}} - \bar{x}\right) \approx 0.95$$

---
# Despejando $\mu$

Multiplicamos por $-1$, lo que **invierte las desigualdades**:

$$P\!\left(\bar{x} + 2\cdot\frac{\sigma}{\sqrt{n}} > \mu > \bar{x} - 2\cdot\frac{\sigma}{\sqrt{n}}\right) \approx 0.95$$

Reordenando de menor a mayor queda la expresión final:

$$\boxed{P\!\left(\bar{x} - 2\cdot\frac{\sigma}{\sqrt{n}} < \mu < \bar{x} + 2\cdot\frac{\sigma}{\sqrt{n}}\right) \approx 0.95}$$

* La media poblacional queda **atrapada** entre dos valores calculables directamente desde la muestra.

---
## Retomando...

Dos herramientas, dos niveles de respuesta.

* La **estimación puntual** da un número: simple, rápida, pero ciega a su propio error.
* La **estimación de intervalo** da un rango: más trabajo, pero con garantía matemática.

Lo que sigue es aprender a construir ese rango según el tamaño de la muestra.

---
<!-- _class: lead -->
# 03
# IC cuando $n \geq 30$
## La distribución normal al rescate.
---
# Fórmulas según nivel de confianza

Cuando $n \geq 30$ o se conoce la varianza poblacional, usamos la distribución normal estándar. El valor de $Z$ se obtiene buscando la probabilidad $\alpha/2$:

| Nivel de confianza | Valor de $Z$ | Fórmula del IC |
|:---:|:---:|:---|
| 90% | 1.64 | $\bar{x} \pm 1.64 \cdot \dfrac{s}{\sqrt{n}}$ |
| 95% | 1.96 | $\bar{x} \pm 1.96 \cdot \dfrac{s}{\sqrt{n}}$ |
| 99% | 2.58 | $\bar{x} \pm 2.58 \cdot \dfrac{s}{\sqrt{n}}$ |

* En la demostración usamos $\approx 2$ como aproximación. El valor preciso de tabla para el 95% es $Z = 1.96$.

---
## Ejemplo: altura media de una planta

Se quiere estimar la altura media de cierta especie. Se toma una muestra de $n = 36$ plantas, se obtiene $\bar{x} = 1.6\ m$ y el desvío estándar poblacional es $\sigma = 0.60\ m$.

**Intervalo de confianza al 95%:**

$$IC(95\%) = 1.6 \pm 1.96 \cdot \frac{0.60}{\sqrt{36}} = 1.6 \pm 1.96 \cdot 0.10 = 1.6 \pm 0.196$$

$$\boxed{IC(95\%) = [1.404\ ;\ 1.796]}$$

* Con un 95% de confianza, la altura media real de la especie se encuentra entre **1.40 m y 1.80 m**.

---
## Los IC en la práctica

Los intervalos de confianza aparecen constantemente en sistemas reales:

* **Encuestas:** "el candidato tiene 42% ± 3 puntos" — es un IC al 95%.
* **Sensores industriales:** calibración con rango de tolerancia garantizado.
* **Machine learning:** intervalos de predicción sobre datos nuevos.
* **Bases de datos distribuidas:** estimación de latencia media con confianza del 99%.

El IC no es un concepto abstracto. Es la forma en que los sistemas comunican **cuánto pueden confiar en sus propios resultados**.

---
<!-- _class: lead -->
# 04
# IC cuando $n < 30$
## Cuando la muestra es pequeña: T de Student.
---
# El problema con muestras chicas

Cuando $n < 30$, **no se conoce la varianza poblacional** y la población tiene distribución **aproximadamente normal**, el TLC no garantiza normalidad suficiente.

En estos casos la distribución adecuada es la **T de Student**: similar a la normal estándar, pero con **colas más pesadas** que reflejan la mayor incertidumbre ante muestras pequeñas.

Depende de los **grados de libertad** $\nu = n - 1$.

$$IC(1-\alpha) = \bar{x} \pm t_{(\nu,\; 1-\alpha/2)} \cdot \frac{s}{\sqrt{n}}$$

---
# Normal estándar vs. T de Student

| Característica | $Z$ Normal | $T$ de Student |
|:---|:---:|:---:|
| Tamaño de muestra | $n \geq 30$ | $n < 30$ |
| Varianza poblacional | Conocida o estimada | Desconocida |
| Colas | Delgadas | Más pesadas |
| Parámetro extra | — | $\nu = n - 1$ |

A medida que $n$ crece, la T de Student **converge** a la distribución normal estándar.

* Con $n$ grande, ambas distribuciones dan resultados prácticamente iguales.

---
## Ejemplo: tiempo de reacción de un fármaco

Se midió el tiempo de reacción de un fármaco en $n = 16$ pacientes: $\bar{x} = 15.4\ h$, $s = 1.5\ h$, distribución aproximadamente normal.

**Grados de libertad:** $\nu = 16 - 1 = 15$

$$\alpha/2 = 0.025 \quad \Rightarrow \quad 1 - \alpha/2 = 0.975 \quad \Rightarrow \quad t_{(15;\; 0.975)} = 2.13$$

$$IC(95\%) = 15.4 \pm 2.13 \cdot \frac{1.5}{\sqrt{16}} = 15.4 \pm 0.80 = \boxed{[14.60\ ;\ 16.20]}$$

---
## El mismo ejemplo: IC al 99%

Con los mismos datos ($n=16$, $\bar{x}=15.4$, $s=1.5$, $\nu=15$):

$$\alpha/2 = 0.005 \quad \Rightarrow \quad 1 - \alpha/2 = 0.995 \quad \Rightarrow \quad t_{(15;\; 0.995)} = 2.95$$

$$IC(99\%) = 15.4 \pm 2.95 \cdot \frac{1.5}{\sqrt{16}} = 15.4 \pm 1.11 = \boxed{[14.29\ ;\ 16.51]}$$

* El IC al 99% es **más ancho** que el de 95%.
* A mayor nivel de confianza, mayor amplitud del intervalo. Siempre hay un trade-off.

---
## Ejemplo: peso de cuatro frutas

Dadas las siguientes mediciones: $28.7,\ 27.9,\ 29.2,\ 26.5\ (gr)$.

**Datos:** $\bar{x} = 28.08$, $s = 1.02$, $n = 4$, $\nu = 3$. Para IC al 95%: $t_{(3;\; 0.975)} = 3.182$

$$\sigma_{\bar{x}} = \frac{s}{\sqrt{n}} = \frac{1.02}{\sqrt{4}} = 0.51$$

$$IC(95\%) = 28.08 \pm 3.182 \cdot 0.51 = \boxed{[26.46\ ;\ 29.70]}$$

* Con 95% de confianza, el peso medio de esa fruta se encuentra entre **26.46 gr y 29.70 gr**.

---
<!-- _class: lead -->
# En resumen...
## ¿Qué herramienta uso?
---
# Guía rápida: estimación puntual vs. intervalo

| Método | Resultado | ¿Cuantifica el error? |
|:---|:---:|:---:|
| Estimación puntual | Un número: $\bar{x}$ | No |
| Intervalo de confianza | Un rango: $[a\ ;\ b]$ | Sí |

La estimación puntual es el punto de partida. El intervalo de confianza es la respuesta completa.

---
# Guía rápida: ¿Z o T?

| Situación | Distribución | Fórmula |
|:---|:---:|:---|
| $n \geq 30$ | $Z$ | $\bar{x} \pm Z \cdot \dfrac{s}{\sqrt{n}}$ |
| $n < 30$, $\sigma$ desconocida, población normal | $T$ | $\bar{x} \pm t_{(\nu)} \cdot \dfrac{s}{\sqrt{n}}$ |

Valores de $Z$: $1.64$ (90%), $1.96$ (95%), $2.58$ (99%).

* Para $T$: consultar tabla con $\nu = n - 1$ grados de libertad.

---
<!-- _class: lead -->
# Cierre

---
# Lo que aprendimos

**Estimación puntual:**
Un único valor $\bar{x}$ que resume la información muestral, pero que no cuantifica su propia precisión.

**Intervalo de confianza:**
Un rango de valores con garantía matemática de contener a $\mu$ el $(1-\alpha)\%$ de las veces.

**IC con distribución Z:**
Cuando $n \geq 30$ o se conoce $\sigma$. Valores clave: 1.64, 1.96, 2.58.

**IC con T de Student:**
Cuando $n < 30$ y $\sigma$ es desconocida. Grados de libertad $\nu = n-1$.

---
# El intervalo como lenguaje

**No es solo una fórmula.**

Es la forma en que la estadística comunica la incertidumbre de forma honesta y precisa.

Cada vez que un laboratorio publica un resultado con margen de error, cada vez que un modelo reporta una predicción con confianza del 95%... hay un intervalo detrás.

---
# Reflexión final

**El azar no desaparece cuando tomamos una muestra.**

**Pero aprendemos a cuantificarlo con precisión.**

No eliminamos la incertidumbre. La medimos, la comunicamos, y tomamos decisiones con ella. Eso es exactamente lo que hace la estadística inferencial.

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"Sin datos, cualquiera es simplemente alguien con una opinión."*
— W. Edwards Deming
