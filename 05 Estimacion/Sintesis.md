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
# 04 — 05
# Inferencia y Estimación
## De la muestra al conocimiento poblacional.
---
La estadística descriptiva nos enseñó a organizar datos. La probabilidad nos dio herramientas para cuantificar el azar.

Ahora viene la pregunta más ambiciosa: **¿podemos conocer una población entera sin estudiarla por completo?**

* ¿Es válido medir unos pocos para hablar de millones?
* ¿Cómo construimos un rango con garantía matemática?
* ¿Qué hacemos cuando la muestra es pequeña?

---
<!-- _class: lead -->
# 01
# Parámetros, Estimadores y Muestreo
## Dos mundos, un vínculo.
---
Antes de inferir, hay que saber exactamente qué estamos estimando y cómo elegimos la muestra.

No toda muestra es válida. Y no todo parámetro se estima igual.

* La elección del estimador depende de la naturaleza de la variable.
* La elección del método de muestreo determina si la inferencia es legítima.

---
# Parámetros y Estimadores

| Parámetro (población) | Estimador (muestra) |
|:---:|:---:|
| Media $\mu$ | Media muestral $\bar{x}$ |
| Desvío estándar $\sigma$ | Desvío muestral $s$ |
| Proporción $P$ | Proporción muestral $\hat{p} = \dfrac{\text{casos}}{n}$ |

* Usamos $\mu$ cuando la variable es **cuantitativa**: queremos saber *cuánto*.
* Usamos $P$ cuando la variable es **cualitativa o binaria**: queremos saber *qué fracción*.

---
# Métodos de Muestreo Aleatorio

Para que la inferencia sea válida, cada individuo debe haber tenido **oportunidad real de ser seleccionado**.

* **Simple:** cada elemento tiene la misma probabilidad de ser elegido.
* **Sistemático:** se elige un punto de partida aleatorio y luego uno cada $k$-ésimo elemento.
* **Estratificado:** se divide la población en subgrupos y se muestrea dentro de cada uno. Garantiza representación de todos.
* **Por conglomeración:** se seleccionan grupos enteros, no elementos individuales.

El **error de muestreo** es la diferencia entre el estadístico y el parámetro. Ningún método lo elimina, pero un buen diseño lo controla.

---
<!-- _class: lead -->
# 02
# Distribución Muestral y TLC
## El resultado más poderoso de la estadística.
---
Si tomamos una muestra y calculamos $\bar{x}$, obtenemos un número.

Si tomamos *todas* las muestras posibles de tamaño $n$, obtenemos una **distribución de probabilidad**.

* Esa distribución tiene su propio valor esperado y su propia variabilidad.
* Y para muestras grandes, tiene una propiedad que lo cambia todo.

---
# Distribución Muestral y Error Estándar

La media de todas las medias muestrales coincide exactamente con $\mu$. Para $n \geq 30$, esa distribución es **siempre normal** sin importar la forma de la población:

$$\boxed{\bar{x} \sim N\!\left(\mu \;;\; \frac{\sigma}{\sqrt{n}}\right)}$$

La cantidad $\sigma_{\bar{x}} = \dfrac{\sigma}{\sqrt{n}}$ es el **error estándar**: mide la variabilidad de las medias muestrales entre sí.

* A mayor $n$, menor error estándar: muestras más grandes producen estimaciones más concentradas alrededor de $\mu$.

---
<!-- _class: lead -->
# 03
# Estimación Puntual e Intervalo de Confianza
## Del número al rango con garantía.
---
# Estimación Puntual e Intervalo de Confianza

Una **estimación puntual** aproxima $\mu$ con un solo valor: $\mu \approx \bar{x}$.

Su limitación: si $\bar{x} = 25.2$, no dice si $\mu$ está a 0.1 o a 20 de distancia.

Una **estimación de intervalo** construye un rango con nivel de confianza $(1-\alpha)$:

$$\boxed{IC(1-\alpha) = \bar{x} \pm Z \cdot \frac{s}{\sqrt{n}}}$$

Un **IC del 95%** significa que el 95% de todos los intervalos construidos de esta manera contendrán al verdadero $\mu$. Es una afirmación sobre el **procedimiento**, no sobre un resultado particular.

---
<!-- _class: lead -->
# 04
# IC según el Tamaño de Muestra
## Z para muestras grandes, T para muestras pequeñas.
---
La herramienta para construir el IC depende de dos factores.

**① ¿Conozco $\sigma$ poblacional?** → Sí: uso **Z**.

**② ¿$n \geq 30$?** → Sí: uso **Z** por el TLC. → No: uso **T-Student**.

* La T-Student requiere asumir que la población de origen es aproximadamente normal.
* Sus grados de libertad son $\nu = n - 1$.

---
# IC con Distribución Z

| Confianza | $Z$ | IC |
|:---:|:---:|:---|
| 90% | 1.64 | $\bar{x} \pm 1.64 \cdot \dfrac{s}{\sqrt{n}}$ |
| 95% | 1.96 | $\bar{x} \pm 1.96 \cdot \dfrac{s}{\sqrt{n}}$ |
| 99% | 2.58 | $\bar{x} \pm 2.58 \cdot \dfrac{s}{\sqrt{n}}$ |

* El valor de $Z$ se obtiene buscando la probabilidad $\alpha/2$ en la tabla normal estándar.

---
## Ejemplo: altura media de una planta

$n = 36$ plantas, $\bar{x} = 1.6\ m$, $\sigma = 0.60\ m$.

$$IC(95\%) = 1.6 \pm 1.96 \cdot \frac{0.60}{\sqrt{36}} = \boxed{[1.404\ ;\ 1.796]}$$

* Con un 95% de confianza, la altura media real de la especie se encuentra entre **1.40 m y 1.80 m**.

---
# IC con T de Student

Cuando $n < 30$ y $\sigma$ es desconocida, la T tiene colas más pesadas que reconocen la mayor incertidumbre:

$$IC(1-\alpha) = \bar{x} \pm t_{(\nu,\; 1-\alpha/2)} \cdot \frac{s}{\sqrt{n}}$$

**Ejemplo:** $n = 16$ pacientes, $\bar{x} = 15.4\ h$, $s = 1.5\ h$, $\nu = 15$.

$$IC(95\%):\ t_{(15;\ 0.975)} = 2.13 \quad \Rightarrow \quad \boxed{[14.60\ ;\ 16.20]}$$

$$IC(99\%):\ t_{(15;\ 0.995)} = 2.95 \quad \Rightarrow \quad \boxed{[14.29\ ;\ 16.51]}$$

* A mayor nivel de confianza, mayor amplitud. Siempre hay un trade-off.

---
<!-- _class: lead -->
# Cierre

---
# Lo que construimos

**Parámetros y muestreo:**
La relación entre lo que existe en la población y lo que medimos en la muestra, y cómo elegir una muestra representativa.

**Distribución muestral y TLC:**
Las medias muestrales se distribuyen normalmente para $n \geq 30$, con error estándar $\sigma/\sqrt{n}$.

---

**Estimación puntual:** Un primer acercamiento a la inferencia, con sus alcances y sus límites.

**Intervalos de confianza:** Z cuando la muestra es grande, T cuando es pequeña.

| Situación | Estadístico |
|:---|:---:|
| $n \geq 30$ o $\sigma$ conocida | $Z$: $1.64\ /\ 1.96\ /\ 2.58$ |
| $n < 30$, $\sigma$ desconocida | $T$: $t_{(\nu = n-1)}$ |

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

*"La estadística es la gramática de la ciencia."*
— Karl Pearson
