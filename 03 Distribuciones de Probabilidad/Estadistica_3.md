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
## Del experimento aleatorio al modelo matemático.
---
En la unidad anterior aprendimos a *cuantificar el azar*.

Ahora queremos ir un paso más allá: **modelarlo**.

* ¿Puede el azar tener una forma predecible?
* ¿Podemos anticipar cómo se comporta una variable antes de medir?
* ¡Sí podemos, y hay modelos matemáticos que lo hacen por nosotros!

---
<!-- _class: lead -->
# 01
# Definiciones Iniciales
## Antes de modelar, hay que hablar el mismo idioma.
---
# Variable Aleatoria

Una **variable aleatoria** es toda función que asocia a cada elemento del espacio muestral un número real.

* Se escriben con letras mayúsculas: $X$, $Y$, $Z$...
* Sus valores concretos con minúsculas: $x$, $y$, $z$...

**Ejemplo:** al elegir 10 peces al azar de un arroyo, se pueden definir múltiples V.A. sobre el mismo experimento:

$$X: \text{cantidad de machos} \quad W: \text{peso promedio} \quad Z: \text{cantidad de sanos}$$

---
# Discreta vs. Continua

**Variable aleatoria discreta:** toma un número *finito* de valores entre dos cualesquiera.

* La puntuación al tirar un dado.
* El número de crías de una especie.

**Variable aleatoria continua:** puede tomar un número *infinito* de valores entre dos cualesquiera.

* La altura de los alumnos de una clase.
* Las horas de duración de una pila.

---
# Distribución de Probabilidad

Se llama **distribución de probabilidad** de una V.A. discreta $X$ a la función que asocia a cada valor $x_i$ su probabilidad $p_i = P(X = x_i)$.

Condiciones que siempre deben cumplirse:

$$0 \leq p_i \leq 1 \qquad \text{y} \qquad \sum p_i = 1$$

* Si no se cumplen ambas condiciones, no es una distribución de probabilidad válida.

---
# Función de Distribución Acumulada

La **función de distribución acumulada** $F(x_i)$ asocia a cada valor $x_i$ la probabilidad de que $X$ sea *menor o igual* a ese valor:

$$F(x_i) = P(X \leq x_i)$$

**Ejemplo con el dado:**

$$F(4) = P(X \leq 4) = P(X=1) + P(X=2) + P(X=3) + P(X=4) = \frac{4}{6}$$

* La distribución acumulada no reemplaza a la distribución: son dos herramientas complementarias.

---
# Parámetros de una V.A. Discreta

**Esperanza matemática (media):**
$$E(X) = \mu = \sum_{i=1}^{n} x_i \cdot p_i$$

**Varianza** (dos formas equivalentes):
$$\sigma^2 = \sum_{i=1}^{n} (x_i - \mu)^2 \cdot p_i \qquad \text{o bien} \qquad \sigma^2 = \sum_{i=1}^{n} x_i^2 \cdot p_i - \mu^2$$

**Desviación típica:**
$$\sigma = \sqrt{\sigma^2}$$

---
## Ejemplo: suma de dos dados

La suma de dos dados tiene dominio $D_X = \{2, 3, \ldots, 12\}$.

| $X$ | $p_i$ | $F(x_i)$ | | $X$ | $p_i$ | $F(x_i)$ |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 2 | 0.028 | 0.028 | | 8 | 0.139 | 0.722 |
| 3 | 0.056 | 0.083 | | 9 | 0.111 | 0.833 |
| 4 | 0.083 | 0.167 | | 10 | 0.083 | 0.917 |
| 5 | 0.111 | 0.278 | | 11 | 0.056 | 0.972 |
| 6 | 0.139 | 0.417 | | 12 | 0.028 | 1.000 |
| 7 | **0.167** | **0.583** | | | | |

El **7** es el valor más probable y también el valor esperado: $E(X) = 7$.

---
## Usando la función acumulada

La acumulada nos permite calcular probabilidades de intervalos sin sumar caso por caso:

$$P(5 \leq X \leq 7) = F(7) - F(4) = 0.583 - 0.167 = \boxed{0.416}$$

$$P(X > 7) = 1 - F(7) = 1 - 0.583 = \boxed{0.417}$$

* Se resta la acumulada del valor límite inferior al del límite superior.
* Siempre hay que prestar atención a si el intervalo es abierto o cerrado.

---
<!-- _class: lead -->
# 02
# Modelos para Variables Discretas
## Cuando el experimento encaja en un patrón.
---
Existen muchos tipos de distribuciones que pueden explicar el comportamiento de una V.A.

En esta unidad nos concentramos en **cinco**:

* **Uniforme** → todos los resultados son igualmente probables.
* **Bernoulli** → el ladrillo fundamental.
* **Binomial** → Bernoulli repetida $n$ veces.
* **Poisson** → eventos raros en un intervalo.
* **Normal** → la distribución reina de las continuas.

---
<!-- _class: lead -->
# Distribución Uniforme
## Cuando el azar no tiene preferencias.
---
# Distribución Uniforme

El modelo más simple posible: **todos los resultados son igualmente probables**.

$$P(X = x_i) = \frac{1}{k} \quad \text{para todo } x_i \in \{x_1, x_2, \ldots, x_k\}$$

**Ejemplo:** al lanzar un dado, cada cara tiene probabilidad $\frac{1}{6}$.

| $x$ | 1 | 2 | 3 | 4 | 5 | 6 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| $p_i$ | 1/6 | 1/6 | 1/6 | 1/6 | 1/6 | 1/6 |

* Es el punto de partida. De acá en adelante, los modelos se vuelven más específicos y más potentes.

---
<!-- _class: lead -->
# Distribución de Bernoulli
## El resultado tiene solo dos caras.
---
# Bernoulli

Un experimento sigue el modelo de **Bernoulli** si cumple cuatro condiciones:

1. Solo hay **dos resultados posibles**: éxito $A$ o fracaso $\bar{A}$.
2. Las probabilidades $p$ (éxito) y $q$ (fracaso) son **constantes**.
3. Se cumple que $p + q = 1$, es decir, $q = 1 - p$.
4. El resultado de cada prueba es **independiente** de las anteriores.

---
## Bernoulli en la vida cotidiana

* Lanzar una moneda: cara o cruz.
* Un paciente responde o no a un tratamiento.
* Un paquete de red llega o se pierde.
* Un proceso de compilación termina con error o sin él.

Bernoulli es el **átomo** de los modelos probabilísticos. Todo lo que sigue se construye sobre él.

---
<!-- _class: lead -->
# Distribución Binomial
## Bernoulli repetida $n$ veces.
---
# Distribución Binomial

La binomial describe experimentos con **$n$ pruebas Bernoulli idénticas e independientes**.

La variable aleatoria $X$ es el **número de éxitos** en esas $n$ pruebas:

$$P(X = x) = \binom{n}{x} \cdot p^x \cdot q^{n-x} \qquad X \sim B(n,\ p)$$

Sus parámetros son:

$$E(X) = n \cdot p \qquad \sigma^2 = n \cdot p \cdot q \qquad \sigma = \sqrt{n \cdot p \cdot q}$$

---
## Ejemplo: el examen al azar

Examen de 10 preguntas con 4 opciones. Sin estudiar nada, $p = 0.25$ y $q = 0.75$.

¿Cuál es la probabilidad de aprobar (6 o más correctas)?

$$X \sim B(10,\ 0.25) \qquad E(X) = 10 \cdot 0.25 = 2.5$$

$$P(X \geq 6) = 1 - P(X \leq 5) = 1 - 0.980 = \boxed{0.02}$$

* Solo el **2% de probabilidad** de aprobar al azar. Las probabilidades no mienten.

---
## Dentro del examen: exactamente 6 correctas

¿Cuántas combinaciones de 6 correctas sobre 10 existen?

$$\binom{10}{6} = 210 \text{ combinaciones posibles}$$

La probabilidad de una de ellas (6 éxitos, 4 fracasos):

$$p^6 \cdot q^4 = 0.25^6 \cdot 0.75^4 = 0.0000772$$

$$P(X=6) = 210 \cdot 0.0000772 = \boxed{0.016}$$

* El complemento $1 - F(5)$ es más rápido, pero este desarrollo muestra de dónde sale la fórmula.

---
<!-- _class: lead -->
# Distribución de Poisson
## Cuando los eventos son raros pero contables.
---
# Distribución de Poisson

La distribución de **Poisson** modela cuántas veces ocurre un evento *infrecuente* en un intervalo de **tiempo dado o en una región específica**.

El parámetro $\lambda$ es la **tasa media de ocurrencia** en ese intervalo:

$$P(X = x) = \frac{e^{-\lambda} \cdot \lambda^x}{x!} \qquad x = 0, 1, 2, \ldots$$

Media y varianza coinciden: $\mu = \lambda$ y $\sigma^2 = \lambda$

---
## ¿Cuándo aplicar Poisson?

Es una buena aproximación a la Binomial cuando $n$ es grande y $p$ muy pequeña.

**Regla práctica:** $np \leq 5$

Ejemplos de sucesos "raros":

* Cantidad de mutaciones en una cadena de ADN.
* Número de pacientes que llegan por hora a una guardia.
* Núcleos atómicos inestables que se desintegran en un período dado.
* Errores de transmisión en una red por segundo.

---
## Ejemplo: pacientes en una guardia

En promedio llegan **4 pacientes por hora** a una guardia. ¿Cuál es la probabilidad de que en una hora lleguen exactamente 2?

$$\lambda = 4 \qquad X \sim Poisson(4)$$

$$P(X = 2) = \frac{e^{-4} \cdot 4^2}{2!} = \frac{0.0183 \cdot 16}{2} = \boxed{0.147}$$

* Hay un 14.7% de probabilidad de que lleguen exactamente 2 pacientes en esa hora.
* El valor más probable sigue siendo $\lambda = 4$, que es la media del modelo.

---
## Poisson en informática

El modelo de Poisson aparece constantemente en sistemas reales:

* **Redes:** modelado del tráfico de paquetes y colas de espera.
* **Sistemas operativos:** procesos que llegan al scheduler.
* **Seguridad:** detección de eventos anómalos e intrusiones.
* **Bases de datos:** transacciones concurrentes por intervalo.

El azar no es solo académico. Es la base de cómo diseñamos sistemas que funcionan bajo incertidumbre.

---
## Retomando...

Tres modelos discretos, tres formas distintas de ver el mismo fenómeno.

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
En las distribuciones discretas contábamos.

En las continuas **medimos**: pesos, tiempos, temperaturas, distancias.

* La probabilidad ya no se calcula en puntos sino como **área bajo una curva**.
* La herramienta central es la **función de densidad**.
* Y el modelo más importante de todos tiene nombre propio.

---
<!-- _class: lead -->
# Distribución Normal
## La campana que lo explica casi todo.
---
# ¿Por qué importa tanto la Normal?

La distribución normal es la base de la inferencia estadística.

* Aparece de forma natural en errores de medición, alturas, pesos, tiempos de respuesta.
* Es una buena aproximación a la Binomial para muestras grandes.
* Los métodos de estimación e hipótesis que veremos en la Unidad 4 se apoyan en ella.

**Definición:** $X \sim N(\mu,\ \sigma)$ con función de densidad:

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} \cdot e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

---
# Propiedades de la Distribución Normal

* El área total bajo la curva de Gauss es igual a **1**.
* La media, mediana y moda son **iguales** entre sí.
* Es **simétrica** en torno a la media $\mu$.
* Toma su valor máximo en $\mu$ y los puntos de inflexión están en $\mu \pm \sigma$.
* El eje $x$ es **asíntota** de la curva.
* Crece antes de $\mu$ y decrece después.

---
## Una advertencia importante

**No todo lo que tiene forma de campana es normal.**

Existen otras distribuciones con curvas similares, como la **distribución t de Student** (que estudiaremos más adelante).

La forma de la curva no es suficiente para determinar la distribución.

* Al modelar datos reales, siempre hay que verificar el ajuste, no asumir normalidad por la forma visual.

---
## La Regla Empírica

La relación entre $\sigma$ y la probabilidad es fija para toda distribución normal:

| Intervalo | Probabilidad |
|:---:|:---:|
| $\mu \pm 1\sigma$ | 68% |
| $\mu \pm 2\sigma$ | 95% |
| $\mu \pm 3\sigma$ | 99.7% |
| $\mu \pm 4\sigma$ | 99.994% |
| $\mu \pm 5\sigma$ | 99.99994% |
| $\mu \pm 6\sigma$ | 99.9999998% |

* La regla de los **6 sigma** es el estándar de calidad de la industria. 

---
<!-- _class: lead -->
# Distribución Normal Estándar
## Traducir para poder consultar la tabla.
---
# Normal Estándar: $Z \sim N(0, 1)$

La **distribución normal estándar** tiene media $\mu = 0$ y desviación típica $\sigma = 1$.

Su función de densidad propia es:

$$f(x) = \frac{1}{\sqrt{2\pi}} \cdot e^{-\frac{x^2}{2}}$$

Para transformar cualquier variable normal en estándar se **tipifica**:

$$Z = \frac{x - \mu}{\sigma}$$

El valor $z$ indica **cuántos desvíos** se aleja un valor determinado de la media.

---
## Ejemplo: peso de una especie

Una especie pesa en promedio $\mu = 36\ kg$ con $\sigma = 3\ kg$.

**Un ejemplar de 39 kg:**
$$z = \frac{39 - 36}{3} = 1 \quad \Rightarrow \quad \text{a un desvío por encima de la media}$$

**Un ejemplar de 30 kg:**
$$z = \frac{30 - 36}{3} = -2 \quad \Rightarrow \quad \text{a dos desvíos por debajo de la media}$$

---
## Usando la tabla Z

Con los valores tipificados, consultamos la tabla (Libro Daniel, Tabla C, pág. 821-822):

$$P(Z < 1) = 0.8413 \quad \Rightarrow \quad \text{84\% de probabilidad de pesar menos de 39 kg}$$

$$P(Z < -2) = 0.0228 \quad \Rightarrow \quad \text{solo 2\% de probabilidad de pesar menos de 30 kg}$$

$$P(-2 < Z < 1) = 0.8413 - 0.0228 = \boxed{0.8186}$$

Un 82% de los ejemplares pesa entre 30 y 39 kg.

---
## Los valores que hay que recordar

Tres valores de $z$ que aparecen en todos los problemas de acá en adelante:

| $z$ | Probabilidad central |
|:---:|:---:|
| $\pm 1$ | 68% |
| $\pm 1.96$ | 95% |
| $\pm 2.58$ | 99% |

* Estos números son la puerta de entrada a la **inferencia estadística**. (más de esto en la Unidad 4)

---
<!-- _class: lead -->
# En resumen...
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
<!-- _class: lead -->
# Cierre

---
# Lo que aprendimos

**Variable aleatoria:**
Traducir resultados de experimentos a números con los que podemos operar matemáticamente.

**Distribución y función acumulada:**
Dos formas complementarias de describir el comportamiento probabilístico de una variable.

**Modelos discretos:**
Uniforme, Bernoulli, Binomial y Poisson para contar y modelar eventos.

**Distribución Normal:**
El modelo continuo más importante, base de la inferencia estadística.

---
# Las distribuciones como lenguaje

**No son solo fórmulas.**

Son modelos que describen cómo se comporta el mundo cuando no podemos predecirlo con certeza.

Cada vez que un sistema detecta anomalías, cada vez que un modelo clasifica, cada vez que se estima una confianza... hay una distribución de probabilidad detrás.

---
# Reflexión final

**La distribución normal no es perfecta.**

**Pero es sorprendentemente buena describiendo un mundo imperfecto.**

Y cuando no alcanza, tenemos Poisson, Binomial, y docenas de modelos más esperando ser usados.

En probabilidad no eliminamos el azar. **Aprendemos a convivir con él de forma inteligente.**

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"Todos los modelos son incorrectos, pero algunos son útiles."*
— George Box
