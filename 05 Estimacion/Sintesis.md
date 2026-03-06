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
# Unidades 04 y 05
# Distribución Muestral e Inferencia
## De la muestra al conocimiento poblacional.

---
# ¿Por qué no hacemos siempre un censo?

El **censo es costoso, lento y a veces imposible**.

- El Censo Nacional de Argentina se realiza **cada 10 años**.
- En estudios médicos, industriales o científicos, estudiar a toda la población es **inviable**.

La solución: trabajar con **muestras**.

La estadística inferencial nos dice **cómo hacerlo con rigor matemático**.

---
<!-- _class: lead -->
# 01
# Parámetros y Estimadores
## Dos mundos, un vínculo.

---
# El vocabulario fundamental

| Parámetro (población) | Estimador (muestra) | Se usa para… |
|:---:|:---:|:---:|
| Media poblacional $\mu$ | Media muestral $\bar{x}$ | Variables cuantitativas (*¿cuánto?*) |
| Desvío estándar $\sigma$ | Desvío muestral $s$ | Variabilidad |
| Proporción poblacional $P$ | Proporción muestral $\hat{p}$ | Variables cualitativas/binarias (*¿qué fracción?*) |

**Distinción clave:** $\mu$ es un valor **fijo** que existe en la población. $\bar{x}$ es una **variable aleatoria**: cada muestra produce un valor distinto — y eso es exactamente lo que hace posible la inferencia.

---
<!-- _class: lead -->
# 02
# Métodos de Muestreo Aleatorio
## No todas las muestras se toman igual.

---
# Tipos de muestreo (I)

**Aleatorio simple:** cada elemento tiene la **misma probabilidad** de ser seleccionado. Es el método base que sustenta toda la teoría estadística.

**Sistemático:** se elige un punto de partida aleatorio y se selecciona **uno cada $k$-ésimo elemento**.
- Ej.: de 1000 personas, elijo una al azar entre las primeras 10 y luego cada 10 desde ahí.

---
# Tipos de muestreo (II)

**Estratificado:** se divide la población en **estratos** homogéneos y se toma muestra de cada uno. Garantiza representación de todos los subgrupos.

**Por conglomeración:** se seleccionan **grupos enteros** — no elementos individuales de cada grupo. Útil cuando la población está naturalmente agrupada (escuelas, barrios, empresas).

> El **error de muestreo** es inevitable, pero un buen diseño lo controla.

---
<!-- _class: lead -->
# 03
# Distribución de Muestreo de Medias
## ¿Qué pasa si tomamos muchas muestras?

---
# La pregunta que cambia todo

Si tomamos *todas* las muestras posibles de tamaño $n$ y calculamos cada $\bar{x}$, obtenemos una **distribución de probabilidad** de todas las medias posibles.

$$\text{Población} \xrightarrow{\text{Muestra 1}} \bar{x}_1,\quad \xrightarrow{\text{Muestra 2}} \bar{x}_2,\quad \ldots \longrightarrow \text{Distribución muestral de } \bar{x}$$

**Propiedad fundamental — siempre se cumple:**

$$\mu_{\bar{x}} = \mu$$

La media de todas las medias muestrales **es igual** a la media poblacional, independientemente del tamaño de la población o la forma de su distribución.

---
<!-- _class: lead -->
# 04
# Teorema del Límite Central
## El resultado más poderoso de la estadística.

---
# Teorema del Límite Central (TLC)

Para cualquier población con media $\mu$ y desvío $\sigma$, si $n \geq 30$:

$$\boxed{\bar{x} \sim N\!\left(\mu_{\bar{x}} = \mu \;;\; \sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}\right)}$$

- **No importa** la forma de la distribución original de la población.
- Con $n \geq 30$, las medias muestrales **siempre** se distribuyen normalmente.

---
# El error estándar

$$\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$$

- $\sigma$ mide la variabilidad de los **datos individuales**.
- $\sigma_{\bar{x}}$ mide la variabilidad de las **medias muestrales** entre sí.

A mayor $n$, menor error estándar: **muestras más grandes → estimaciones más precisas**.

---
<!-- _class: lead -->
# 05
# Estimación Puntual
## Un primer paso hacia la inferencia.

---
# Estimación puntual

Un **único valor** calculado desde la muestra para aproximar un parámetro poblacional.

$$\mu \approx \bar{x} \qquad \sigma \approx s \qquad P \approx \hat{p}$$

**Ventaja:** simple, directa y fácil de comunicar.

**Limitación fundamental:** no dice **cuán precisa** es esa estimación.

> ¿Está $\mu$ a 0.1 de distancia? ¿A 5? ¿A 20?
> La estimación puntual sola **no puede responder eso**.

Para eso necesitamos un rango — y garantía matemática de que ese rango tiene sentido.

---
<!-- _class: lead -->
# 06
# Intervalo de Confianza
## Un rango con garantía matemática.

---
# Intervalo de Confianza (IC)

Un **rango de valores** construido desde la muestra que, con nivel de confianza $(1-\alpha)$, contiene al verdadero parámetro $\mu$.

> $\alpha$ es el **nivel de significancia**: la probabilidad de que el intervalo *no* contenga a $\mu$. Si $\alpha = 0.05$, el IC es del 95%.

$$\boxed{IC(1-\alpha) = \bar{x} \pm Z \cdot \frac{s}{\sqrt{n}}}$$

*Origen:* por el TLC, $P\!\left(\bar{x} - Z\tfrac{\sigma}{\sqrt{n}} < \mu < \bar{x} + Z\tfrac{\sigma}{\sqrt{n}}\right) = 1-\alpha$. Se despeja $\mu$ del centro y se obtiene la fórmula.

---

**Interpretación correcta:** el 95% de todos los intervalos construidos de esta manera **contendrán** a $\mu$ — es una afirmación sobre el **procedimiento**, no sobre un resultado particular.

---
<!-- _class: lead -->
# 07
# IC con Distribución $Z$
## Cuando $n \geq 30$

---
# Fórmulas según nivel de confianza

| Nivel de confianza | Valor de $Z$ | Fórmula del IC |
|:---:|:---:|:---|
| 90% | 1.64 | $\bar{x} \pm 1.64 \cdot \dfrac{s}{\sqrt{n}}$ |
| 95% | 1.96 | $\bar{x} \pm 1.96 \cdot \dfrac{s}{\sqrt{n}}$ |
| 99% | 2.58 | $\bar{x} \pm 2.58 \cdot \dfrac{s}{\sqrt{n}}$ |

El valor $Z$ se obtiene de la tabla normal estándar buscando la probabilidad $\alpha/2$.

---
# Ejemplo: altura media de una planta

$n = 36$, $\bar{x} = 1.6\ m$, $\sigma = 0.60\ m$

$$IC(95\%) = 1.6 \pm 1.96 \cdot \frac{0.60}{\sqrt{36}} = \boxed{[1.404\ ;\ 1.796]\ m}$$

$$IC(99\%) = 1.6 \pm 2.58 \cdot \frac{0.60}{\sqrt{36}} = \boxed{[1.342\ ;\ 1.858]\ m}$$

> Mayor confianza → intervalo más ancho. Siempre hay un **trade-off** entre precisión y certeza.

---
<!-- _class: lead -->
# 08
# IC con T de Student
## Cuando $n < 30$

---
# El problema con muestras pequeñas

Cuando $n < 30$, $\sigma$ desconocida y población aproximadamente normal:

- El TLC no garantiza normalidad suficiente.
- La distribución adecuada es la **T de Student**: colas más pesadas que reflejan la mayor incertidumbre.

$$\boxed{IC(1-\alpha) = \bar{x} \pm t_{(\nu,\; 1-\alpha/2)} \cdot \frac{s}{\sqrt{n}}}$$

Donde $\nu = n - 1$ son los **grados de libertad**.

---
# Normal estándar vs. T de Student

| Característica | $Z$ Normal | $T$ de Student |
|:---|:---:|:---:|
| Tamaño de muestra | $n \geq 30$ | $n < 30$ |
| Varianza poblacional | Conocida o estimada | Desconocida |
| Colas | Delgadas | Más pesadas |
| Parámetro extra | — | $\nu = n - 1$ |

A medida que $n$ crece, $T$ **converge** a $Z$.

---
# Ejemplo: tiempo de reacción de un fármaco

$n = 16$, $\bar{x} = 15.4\ h$, $s = 1.5\ h$ → $\nu = 15$

**IC al 95%:** $t_{(15;\; 0.975)} = 2.13$

$$IC(95\%) = 15.4 \pm 2.13 \cdot \frac{1.5}{\sqrt{16}} = \boxed{[14.60\ ;\ 16.20]\ h}$$

**IC al 99%:** $t_{(15;\; 0.995)} = 2.95$

$$IC(99\%) = 15.4 \pm 2.95 \cdot \frac{1.5}{\sqrt{16}} = \boxed{[14.29\ ;\ 16.51]\ h}$$

> Mayor nivel de confianza → intervalo más ancho. Siempre hay un **trade-off**.

---
<!-- _class: lead -->
# 09
# Guía de Decisión
## ¿Qué herramienta uso?

---
# ¿Estimación puntual o IC? ¿Z o T?

| Situación | Herramienta | Resultado |
|:---|:---:|:---:|
| Quiero un único número rápido | Estimación puntual $\bar{x}$ | Sin medida de error |
| $n \geq 30$ | IC con $Z$ | Rango al nivel $(1-\alpha)$ |
| $n < 30$, $\sigma$ desconocida, pop. normal | IC con $T$ | Rango al nivel $(1-\alpha)$ |

**Valores de $Z$:** $1.64$ (90%) · $1.96$ (95%) · $2.58$ (99%)

**Para $T$:** consultar tabla con $\nu = n - 1$ grados de libertad.

---
<!-- _class: lead -->
# Cierre

---
# Lo que construimos

| Concepto | Núcleo |
|:---|:---|
| Parámetros y estimadores | $\mu$ es fijo; $\bar{x}$ es variable aleatoria |
| Métodos de muestreo | La representatividad valida la inferencia |
| Distribución de muestreo | $\mu_{\bar{x}} = \mu$ — siempre |
| Teorema del Límite Central | $n \geq 30$ → normalidad garantizada |
| Estimación puntual | Un número sin medida de error |
| Intervalo de confianza | Un rango con garantía matemática |

---
# La idea central

**El azar no desaparece cuando tomamos una muestra.**

**Pero aprendemos a cuantificarlo con precisión.**

No eliminamos la incertidumbre — la medimos, la comunicamos, y tomamos decisiones con ella.

Eso es exactamente lo que hace la estadística inferencial.

> *"Sin datos, cualquiera es simplemente alguien con una opinión."*
> — W. Edwards Deming

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025
