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
# 03
# Distribuciones de Probabilidad
## Síntesis · Del experimento aleatorio al modelo matemático.
---
<!-- _class: lead -->
# 01
# Definiciones Iniciales
## Antes de modelar, hay que hablar el mismo idioma.
---
# Variable Aleatoria

Una **variable aleatoria** es una función que asigna un número real a cada elemento del espacio muestral.

* Se escriben con letras mayúsculas: $X$, $Y$, $Z$
* Sus realizaciones con minúsculas: $x$, $y$, $z$

**Discreta:** finitos valores entre dos cualesquiera → dado, número de crías.

**Continua:** infinitos valores entre dos cualesquiera → altura, tiempo de duración.

---
# Distribución de Probabilidad

Asocia a cada valor $x_i$ su probabilidad $p_i = P(X = x_i)$.

Condiciones obligatorias:
$$0 \leq p_i \leq 1 \qquad \text{y} \qquad \sum p_i = 1$$

**Función acumulada:**
$$F(x_i) = P(X \leq x_i)$$

Permite calcular probabilidades de intervalos sin sumar caso por caso.

---
# Parámetros de una V.A. Discreta

Describen el comportamiento central y la dispersión de la variable.

**Esperanza (media):**
$$E(X) = \mu = \sum x_i \cdot p_i$$

**Varianza:**
$$\sigma^2 = \sum (x_i - \mu)^2 \cdot p_i = \sum x_i^2 \cdot p_i - \mu^2$$

**Desviación típica:**
$$\sigma = \sqrt{\sigma^2}$$

---
<!-- _class: lead -->
# 02
# Modelos para Variables Discretas
## Cuando el experimento encaja en un patrón.
---
# Distribución Uniforme

**Todos los resultados son igualmente probables.**

$$P(X = x_i) = \frac{1}{k}$$

El modelo más simple. Punto de partida antes de los modelos más específicos.

*Ejemplo: cada cara de un dado tiene probabilidad $\frac{1}{6}$.*

---
# Distribución de Bernoulli

Un experimento sigue Bernoulli si:

1. Solo hay **dos resultados**: éxito $A$ o fracaso $\bar{A}$.
2. Las probabilidades $p$ y $q$ son **constantes**.
3. $p + q = 1$
4. Cada prueba es **independiente** de las anteriores.

Es el **átomo** de los modelos probabilísticos. Todo lo que sigue se construye sobre él.

---
# Distribución Binomial

$n$ pruebas Bernoulli idénticas e independientes. $X$ = número de éxitos.

$$P(X = x) = \binom{n}{x} \cdot p^x \cdot q^{n-x} \qquad X \sim B(n,\ p)$$

$$E(X) = n \cdot p \qquad \sigma^2 = n \cdot p \cdot q$$

*Ejemplo: examen de 10 preguntas con 4 opciones, sin estudiar ($p = 0.25$):*
$$P(X \geq 6) = 1 - P(X \leq 5) = \boxed{0.02}$$

Solo el **2% de probabilidad** de aprobar al azar.

---
# Distribución de Poisson

Modela eventos *infrecuentes* en un intervalo de tiempo o región. $\lambda$ = tasa media de ocurrencia.

$$P(X = x) = \frac{e^{-\lambda} \cdot \lambda^x}{x!} \qquad x = 0, 1, 2, \ldots$$

$$\mu = \lambda \qquad \sigma^2 = \lambda$$

**Regla práctica:** buena aproximación a Binomial cuando $n$ grande, $p$ pequeña y $np \leq 5$.

*Ejemplos: paquetes de red perdidos, transacciones concurrentes, eventos anómalos en seguridad.*

---
## Retomando...

Tres modelos discretos, tres formas de ver el mismo fenómeno.

* La **Uniforme** cuando no hay preferencia entre resultados.
* La **Binomial** cuando repetimos una prueba con dos salidas posibles.
* La **Poisson** cuando el evento es raro y ocurre dentro de un intervalo.

Lo que sigue es el salto de lo discreto a lo continuo.

---
<!-- _class: lead -->
# 03
# Modelos para Variables Continuas
## Cuando los valores son infinitos.
---
# Distribución Normal

La distribución más importante. Base de toda la inferencia estadística.

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} \cdot e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2} \qquad X \sim N(\mu,\ \sigma)$$

**Propiedades clave:**
* Simétrica. Media = Mediana = Moda = $\mu$.
* Área total bajo la curva = **1**.
* Puntos de inflexión en $\mu \pm \sigma$.

---
## Una advertencia importante

**No todo lo que tiene forma de campana es normal.**

Existen otras distribuciones con curvas similares, como la **distribución t de Student**.

La forma visual no es suficiente para determinar la distribución. Al modelar datos reales, siempre hay que verificar el ajuste, no asumir normalidad por la apariencia.

---
# La Regla Empírica

| Intervalo | Probabilidad |
|:---:|:---:|
| $\mu \pm 1\sigma$ | 68% |
| $\mu \pm 2\sigma$ | 95% |
| $\mu \pm 3\sigma$ | 99.7% |
| $\mu \pm 6\sigma$ | 99.9999998% |

La regla de los **6 sigma** es el estándar de calidad de la industria.

---
# Normal Estándar y Tipificación

La **normal estándar** tiene $\mu = 0$ y $\sigma = 1$: $Z \sim N(0,\ 1)$.

Para transformar cualquier normal:
$$Z = \frac{x - \mu}{\sigma}$$

*Ejemplo: una especie pesa $\mu = 36\ kg$, $\sigma = 3\ kg$. Un ejemplar de 39 kg:*
$$z = \frac{39 - 36}{3} = 1 \quad \Rightarrow \quad P(Z < 1) = 0.8413$$

El **84%** de los ejemplares pesa menos de 39 kg.

---
## Valores clave de $z$

| $z$ | Probabilidad central |
|:---:|:---:|
| $\pm 1$ | 68% |
| $\pm 1.96$ | 95% |
| $\pm 2.58$ | 99% |

Estos números son la puerta de entrada a la **inferencia estadística**.

---
<!-- _class: lead -->
# En resumen
## ¿Qué modelo uso?
---
# Guía rápida de modelos

| Situación | Modelo |
|:---|:---:|
| Todos los resultados igualmente probables | Uniforme |
| Una sola prueba, éxito o fracaso | Bernoulli |
| $n$ pruebas independientes, cuento éxitos | Binomial |
| Eventos raros en un intervalo, $np \leq 5$ | Poisson |
| Variable continua, fenómeno natural | Normal |

---
# Lo que aprendimos

**Variable aleatoria:** traducir experimentos a números operables matemáticamente.

**Distribución y acumulada:** dos formas complementarias de describir el comportamiento probabilístico.

**Modelos discretos:** Uniforme, Bernoulli, Binomial y Poisson para contar y modelar eventos.

**Distribución Normal:** el modelo continuo más importante, base de la inferencia estadística.

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"Todos los modelos son incorrectos, pero algunos son útiles."*
— George Box
