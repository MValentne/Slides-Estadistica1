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
# Distribución de la Media Muestral
## De la muestra a la población

---

# ¿Por qué trabajar con muestras?

Estudiar a toda una población (censo) es frecuentemente **imposible o inviable** por costo, tiempo o accesibilidad.

La estadística inferencial resuelve esto: permite **obtener conclusiones sobre parámetros poblacionales** usando estadísticos muestrales como puente.

> El Censo Nacional argentino se realiza cada diez años. En ciencia, medicina e industria, esperar eso no es una opción.

---

<!-- _class: lead -->
# Parámetros y Estimadores
## Dos mundos, un vínculo

---

# Parámetros y estimadores

| Parámetro (población) | Estimador (muestra) |
|:---:|:---:|
| Media $\mu$ | Media muestral $\bar{x}$ |
| Desvío estándar $\sigma$ | Desvío muestral $s$ |
| Proporción $P$ | Proporción muestral $\hat{p} = \dfrac{\text{casos con la característica}}{n}$ |

- **$\mu$** → variable cuantitativa: *¿cuánto?*
- **$P$** → variable cualitativa o binaria: *¿qué fracción?*

$\mu$ es un valor **fijo y único** — existe aunque no lo conozcamos. $\bar{x}$ es una **variable aleatoria**: cada muestra produce un valor distinto, con su propia distribución de probabilidad.

> Esto es lo que hace posible toda la inferencia estadística.

---

<!-- _class: lead -->
# Métodos de Muestreo Aleatorio

---

# Tipos de muestreo

| Método | Descripción |
|:---|:---|
| **Simple** | Cada elemento tiene la misma probabilidad de ser elegido |
| **Sistemático** | Se elige uno cada $k$-ésimo elemento desde un inicio aleatorio |
| **Estratificado** | Se divide en subgrupos y se muestrea cada uno — garantiza representación |
| **Por conglomeración** | Se eligen grupos enteros, no elementos individuales |

El **error de muestreo** es la diferencia inevitable entre $\bar{x}$ y $\mu$. No es un error humano: un buen diseño lo *controla*, no lo elimina.

---

<!-- _class: lead -->
# Distribución de Muestreo de Medias

---

# ¿Qué pasa si tomamos muchas muestras?

Si tomamos todas las muestras posibles de tamaño $n$ y calculamos cada $\bar{x}$, obtenemos una **distribución de probabilidad** de esas medias muestrales.

**Propiedad fundamental:**

$$\mu_{\bar{x}} = \mu$$

La media de todas las medias muestrales **siempre** coincide con la media poblacional — para cualquier población y cualquier tamaño de muestra.

---

# Ejemplo: estudio jurídico Hoya & Asociados

5 socios con horas semanales: 22, 26, 30, 26, 22 → $\mu = 25{,}2$

Muestras posibles de tamaño 2: $C_5^2 = 10$

| $\bar{x}$ | Frec. relativa |
|:---:|:---:|
| 22 | 1/10 |
| 24 | 4/10 |
| 26 | 3/10 |
| 28 | 2/10 |

$$\mu_{\bar{x}} = \frac{22(1)+24(4)+26(3)+28(2)}{10} = 25{,}2 = \mu \checkmark$$

---

<!-- _class: lead -->
# Teorema del Límite Central

---

# El resultado más poderoso de la estadística

Para una población con media $\mu$ y desvío $\sigma$, si $n \geq 30$:

$$\boxed{\bar{x} \sim N\!\left(\mu_{\bar{x}} = \mu \;;\; \sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}\right)}$$

- No importa la forma de la distribución original de la población.
- Para $n \geq 30$, las medias muestrales **siempre** se distribuyen normalmente.

---

# El error estándar

$$\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}$$

| | Mide la variabilidad de… |
|:---|:---|
| $\sigma$ | Los **datos individuales** dentro de la población |
| $\sigma_{\bar{x}}$ | Las **medias muestrales** entre sí |

A medida que $n$ crece, $\sigma_{\bar{x}}$ **disminuye**: muestras más grandes producen estimaciones más concentradas alrededor de $\mu$.

---

<!-- _class: lead -->
# Estimaciones Puntuales
## Un primer paso hacia la inferencia

---

# Estimación puntual y los tres caminos

Una **estimación puntual** es un único valor calculado desde la muestra para aproximar un parámetro poblacional.

| Camino | Método | Resultado |
|:---|:---|:---|
| **Censo** | Calcular $\mu$ sobre toda la población | Exacto, pero costoso o imposible |
| **Estimación puntual** | Calcular $\bar{x}$ sobre una muestra | Rápido, sin medida de confianza |
| **Intervalo de confianza** | Construir un rango probable para $\mu$ | Rápido **y** con grado de confianza |

La estimación puntual es simple y directa — su limitación es que no indica cuán precisa es la estimación.

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **Parámetros y estimadores** | Vincular población y muestra |
| **Métodos de muestreo** | Seleccionar muestras representativas |
| **Distribución de muestreo** | Entender el comportamiento de $\bar{x}$ |
| **TLC** | Garantizar normalidad para $n \geq 30$ |
| **Estimación puntual** | Primer acercamiento a la inferencia |

El TLC es el puente que convierte una muestra en una afirmación rigurosa sobre la población — con error controlado y cuantificable.

> *"La estadística es la gramática de la ciencia."*
> — Karl Pearson

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
