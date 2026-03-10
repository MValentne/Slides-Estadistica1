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
# Distribuciones de Probabilidad
## Del experimento aleatorio al modelo matemático

---

# Variable Aleatoria

Función que asigna un número real a cada elemento del espacio muestral.

| Tipo | Descripción | Ejemplo |
|:---|:---|:---|
| **Discreta** | Finitos valores entre dos cualesquiera | Resultado de un dado |
| **Continua** | Infinitos valores entre dos cualesquiera | Altura, tiempo |

Se escribe con mayúsculas ($X$, $Y$, $Z$); sus realizaciones con minúsculas ($x$, $y$, $z$).

---

# Distribución de Probabilidad y Parámetros

Asocia a cada valor $x_i$ su probabilidad $p_i = P(X = x_i)$, con condiciones:
$$0 \leq p_i \leq 1 \qquad \sum p_i = 1$$

**Función acumulada:** $F(x_i) = P(X \leq x_i)$ — permite calcular probabilidades de intervalos.

**Parámetros:**
$$E(X) = \mu = \sum x_i \cdot p_i \qquad \sigma^2 = \sum x_i^2 \cdot p_i - \mu^2 \qquad \sigma = \sqrt{\sigma^2}$$

---

<!-- _class: lead -->
# Modelos para Variables Discretas

---

# Modelos base: Uniforme y Bernoulli

**Uniforme** — todos los resultados son igualmente probables:
$$P(X = x_i) = \frac{1}{k}$$
*Ejemplo: cada cara de un dado tiene probabilidad $\frac{1}{6}$.*

**Bernoulli** — experimento con exactamente dos resultados posibles:
- Éxito ($p$) o fracaso ($q = 1 - p$), pruebas independientes
- Es el **átomo** de los modelos probabilísticos — todo lo que sigue se construye sobre él

---

# Distribución Binomial

$n$ pruebas Bernoulli idénticas e independientes. $X$ = número de éxitos.

$$P(X = x) = \binom{n}{x} \cdot p^x \cdot q^{n-x} \qquad X \sim B(n,\ p)$$

$$E(X) = n \cdot p \qquad \sigma^2 = n \cdot p \cdot q$$

*Ejemplo: examen de 10 preguntas con 4 opciones, sin estudiar ($p = 0{,}25$):*

$$P(X \geq 6) = 1 - P(X \leq 5) = \boxed{0{,}02}$$

Solo el **2%** de probabilidad de aprobar al azar.

---

# Distribución de Poisson

Modela eventos **infrecuentes** en un intervalo de tiempo o región. $\lambda$ = tasa media de ocurrencia.

$$P(X = x) = \frac{e^{-\lambda} \cdot \lambda^x}{x!} \qquad \mu = \lambda \qquad \sigma^2 = \lambda$$

**Regla práctica:** buena aproximación a Binomial cuando $n$ grande, $p$ pequeña y $np \leq 5$.

*Ejemplos: paquetes de red perdidos, transacciones concurrentes, eventos anómalos en seguridad.*

---

<!-- _class: lead -->
# Modelos para Variables Continuas

---

# Distribución Normal

La distribución más importante. Base de toda la inferencia estadística.

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} \cdot e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2} \qquad X \sim N(\mu,\ \sigma)$$

**Propiedades clave:**
- Simétrica — Media = Mediana = Moda = $\mu$
- Área total bajo la curva = **1**
- La curva cambia de "curvatura" en los puntos μ±σ\mu \pm \sigma μ±σ, es decir, donde la campana pasa de cerrarse hacia el centro a abrirse hacia los costados


---

# Regla Empírica

| Intervalo | Probabilidad |
|:---:|:---:|
| $\mu \pm 1\sigma$ | 68% |
| $\mu \pm 2\sigma$ | 95% |
| $\mu \pm 3\sigma$ | 99,7% |
| $\mu \pm 6\sigma$ | 99,9999998% |

La regla de los **6 sigma** es el estándar de calidad de la industria.

> No todo lo que tiene forma de campana es normal — siempre verificar el ajuste, no asumir por apariencia.

---

# Normal Estándar y Tipificación

La **normal estándar** tiene $\mu = 0$ y $\sigma = 1$: $Z \sim N(0,\ 1)$.

Transformación (tipificación):
$$Z = \frac{x - \mu}{\sigma}$$

*Ejemplo: especie con $\mu = 36\ \text{kg}$, $\sigma = 3\ \text{kg}$. Un ejemplar de 39 kg:*

$$z = \frac{39 - 36}{3} = 1 \quad \Rightarrow \quad P(Z < 1) = 0{,}8413$$

El **84%** de los ejemplares pesa menos de 39 kg.

| $z$ | $\pm 1{,}00$ | $\pm 1{,}96$ | $\pm 2{,}58$ |
|:---|:---:|:---:|:---:|
| Prob. central | 68% | 95% | 99% |

---

<!-- _class: lead -->
# Guía de Selección de Modelos

---

# ¿Qué modelo uso?

| Situación | Modelo |
|:---|:---:|
| Resultados igualmente probables | Uniforme |
| Una prueba, éxito o fracaso | Bernoulli |
| $n$ pruebas independientes, cuento éxitos | Binomial |
| Eventos raros en un intervalo, $np \leq 5$ | Poisson |
| Variable continua, fenómeno natural | Normal |

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **Variable aleatoria** | Traducir experimentos a números operables |
| **Distribución y acumulada** | Describir el comportamiento probabilístico |
| **Modelos discretos** | Uniforme, Bernoulli, Binomial, Poisson |
| **Distribución Normal** | El modelo continuo más importante |

---

Los modelos no son la realidad — son **aproximaciones útiles** que permiten razonar con rigor sobre fenómenos inciertos.

> *"Todos los modelos son incorrectos, pero algunos son útiles."*
> — George Box

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
