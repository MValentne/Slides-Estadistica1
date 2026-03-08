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
# Estimación de la Media Poblacional
## Del dato muestral al conocimiento poblacional

---

# Estimación puntual

Un único valor calculado desde la muestra para aproximar un parámetro poblacional:

$$\mu \approx \bar{x} \qquad \sigma \approx s \qquad P \approx \hat{p}$$

**Ventaja:** simple y directa.

**Limitación fundamental:** no dice nada sobre su propia precisión.

> Si $\bar{x} = 25{,}2$, ¿está $\mu$ a 0,1 de distancia? ¿A 5? ¿A 20? La estimación puntual sola **no puede responder eso**.

---

<!-- _class: lead -->
# Intervalos de Confianza

---

# ¿Qué es un Intervalo de Confianza?

Un rango de valores construido desde la muestra que contiene al parámetro $\mu$ con una probabilidad $(1-\alpha)$.

$$\boxed{IC(1-\alpha) = \bar{x} \pm Z \cdot \frac{s}{\sqrt{n}}}$$

**Interpretación correcta:** el 95% de todos los intervalos construidos con este procedimiento contienen al verdadero $\mu$.

> No es una afirmación sobre un resultado particular — es una afirmación sobre el **procedimiento**.

---

# Demostración del IC al 95%

Por el TLC, el 95% de las medias muestrales satisface:

$$P\!\left(\mu - 1{,}96\cdot\frac{\sigma}{\sqrt{n}} < \bar{x} < \mu + 1{,}96\cdot\frac{\sigma}{\sqrt{n}}\right) \approx 0{,}95$$

Despejando $\mu$ (restando $\bar{x}$, multiplicando por $-1$ e invirtiendo desigualdades):

$$\boxed{P\!\left(\bar{x} - 1{,}96\cdot\frac{\sigma}{\sqrt{n}} < \mu < \bar{x} + 1{,}96\cdot\frac{\sigma}{\sqrt{n}}\right) \approx 0{,}95}$$

$\mu$ queda **atrapada** entre dos valores calculables directamente desde la muestra.

---

<!-- _class: lead -->
# IC con Distribución $Z$ — $n \geq 30$

---

# Fórmulas según nivel de confianza

Cuando $n \geq 30$ o se conoce $\sigma$, se usa la distribución normal estándar.

| Nivel de confianza | $Z$ | Fórmula del IC |
|:---:|:---:|:---|
| 90% | 1,64 | $\bar{x} \pm 1{,}64 \cdot \dfrac{s}{\sqrt{n}}$ |
| 95% | 1,96 | $\bar{x} \pm 1{,}96 \cdot \dfrac{s}{\sqrt{n}}$ |
| 99% | 2,58 | $\bar{x} \pm 2{,}58 \cdot \dfrac{s}{\sqrt{n}}$ |

---

# Ejemplo: altura media de una planta

$n = 36$, $\bar{x} = 1{,}6\ \text{m}$, $\sigma = 0{,}60\ \text{m}$

$$IC(95\%) = 1{,}6 \pm 1{,}96 \cdot \frac{0{,}60}{\sqrt{36}} = 1{,}6 \pm 0{,}196$$

$$\boxed{IC(95\%) = [1{,}404\ ;\ 1{,}796]\ \text{m}}$$

Con 95% de confianza, la altura media real de la especie se encuentra entre **1,40 m y 1,80 m**.

---

<!-- _class: lead -->
# IC con $T$ de Student — $n < 30$

---

# El problema con muestras pequeñas

Cuando $n < 30$ y $\sigma$ es desconocida, el TLC no garantiza normalidad suficiente.

La distribución adecuada es la **T de Student**: similar a la normal estándar, pero con colas más pesadas que reflejan la mayor incertidumbre.

$$IC(1-\alpha) = \bar{x} \pm t_{(\nu,\; 1-\alpha/2)} \cdot \frac{s}{\sqrt{n}} \qquad \nu = n - 1$$

| Característica | $Z$ Normal | $T$ de Student |
|:---|:---:|:---:|
| Tamaño de muestra | $n \geq 30$ | $n < 30$ |
| Varianza poblacional | Conocida o estimada | Desconocida |
| Parámetro extra | — | $\nu = n - 1$ |

---

# Ejemplo: tiempo de reacción de un fármaco

$n = 16$, $\bar{x} = 15{,}4\ \text{h}$, $s = 1{,}5\ \text{h}$, $\nu = 15$

$$t_{(15;\; 0{,}975)} = 2{,}13 \qquad \Rightarrow \qquad IC(95\%) = 15{,}4 \pm 2{,}13 \cdot \frac{1{,}5}{\sqrt{16}}$$

$$\boxed{IC(95\%) = [14{,}60\ ;\ 16{,}20]\ \text{h}}$$

Con los mismos datos, al **99%** ($t_{(15;\;0{,}995)} = 2{,}95$):

$$IC(99\%) = 15{,}4 \pm 2{,}95 \cdot \frac{1{,}5}{\sqrt{16}} = \boxed{[14{,}29\ ;\ 16{,}51]\ \text{h}}$$

> Mayor nivel de confianza → intervalo más ancho. Siempre hay un **trade-off**.

---

<!-- _class: lead -->
# Guía de Decisión

---

# ¿Qué herramienta uso?

| Situación | Distribución | Valores clave |
|:---|:---:|:---|
| $n \geq 30$ | $Z$ | 1,64 · 1,96 · 2,58 |
| $n < 30$, $\sigma$ desconocida, población normal | $T$ | tabla con $\nu = n-1$ |

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **Estimación puntual** | Primer número aproximado, sin medida de error |
| **IC — demostración** | Entender de dónde viene la fórmula |
| **IC con $Z$** | Muestras grandes o $\sigma$ conocida |
| **IC con $T$** | Muestras pequeñas, $\sigma$ desconocida |
| **Trade-off confianza/amplitud** | Mayor confianza implica intervalo más ancho |

El intervalo de confianza no responde *cuál es el valor exacto de $\mu$* — responde *en qué rango podemos confiar que está*, y con qué certeza.

> *"Sin datos, cualquiera es simplemente alguien con una opinión."*
> — W. Edwards Deming

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
