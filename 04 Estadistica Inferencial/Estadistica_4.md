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
# 04
# Distribución de la Media Muestral
## De la muestra a la población.
---
La estadística descriptiva nos enseñó a *organizar* los datos.

La probabilidad nos dio herramientas para *cuantificar* el azar.

Ahora viene la pregunta más ambiciosa: **¿podemos conocer una población entera sin estudiarla por completo?**

* ¿Es válido medir unos pocos para hablar de millones?
* ¿Cómo de confiables serían esas conclusiones?
* La estadística inferencial dice que sí, y lo demuestra con rigor matemático.

---
<!-- _class: lead -->
# Un poco de contexto
## Porque medir todo no siempre es posible.
---
# ¿Por qué no siempre hacemos un censo?

El Censo de Población y Vivienda de Argentina se realiza **cada diez años**.

Requiere equipos en cada localidad y provincia, meses de trabajo y un presupuesto enorme. Aún así, solo se hace una vez por década.

* En la mayoría de estudios científicos, médicos o industriales, es **físicamente imposible** estudiar a toda la población.
* Cuando es posible, el **costo económico** lo hace inviable.
* La solución es trabajar con **muestras**, y la estadística inferencial nos dice cómo hacerlo bien.

---
La estadística inferencial paramétrica tiene exactamente ese fin: **obtener conclusiones sobre parámetros poblacionales** usando como puente los estadísticos muestrales, sus distribuciones en el muestreo, y herramientas como el Teorema del Límite Central, el error estándar y los intervalos de confianza.

---
<!-- _class: lead -->
# 00
# Parámetros y Estimadores
## Dos mundos, un vínculo.
---
# El vocabulario fundamental

| Parámetro (población) | Estimador (muestra) |
|:---:|:---:|
| Media poblacional $\mu$ | Media muestral $\bar{x}$ |
| Desvío estándar $\sigma$ | Desvío muestral $s$ |
| Proporción poblacional $P$ | Proporción muestral $\hat{p}$ |

En Estadística I nos concentraremos en la **media poblacional** y su estimador, sin perder de vista que existen otros parámetros con sus propios estimadores específicos.

---
Hay una diferencia clave que no se puede perder de vista.

La **media poblacional** $\mu$ es un valor fijo y único en un momento dado: existe ahí afuera, aunque no lo conozcamos directamente.

La **media muestral** $\bar{x}$ es una **variable aleatoria continua**: cada muestra aleatoria produce un valor distinto. Por lo tanto, puede responder a una distribución de probabilidad con su valor esperado y su medida de variabilidad.

* Esto es lo que hace posible toda la inferencia que viene después.

---
<!-- _class: lead -->
# 01
# Métodos de Muestreo Aleatorio
## No todas las muestras se toman igual.
---
# ¿Qué hace válido un muestreo?

Para que las conclusiones de una muestra sean válidas, cada individuo de la población tiene que haber tenido **una oportunidad real de ser seleccionado**.

A eso lo llamamos **muestreo aleatorio**, y tiene varias formas según el contexto.

**Muestra aleatoria simple:** cada elemento de la población tiene la **misma probabilidad** de quedar incluido.
- Es el método más puro y el que sustenta la mayor parte de la teoría estadística.

---
**Muestra aleatoria sistemática:** los individuos se ordenan, se elige un punto de partida aleatorio y luego se selecciona **uno cada k-ésimo elemento**.
- Si tengo 1000 personas y quiero una muestra de 100, tomo una al azar entre las primeras 10 y luego cada 10 desde ahí.

**Muestreo aleatorio estratificado:** se divide la población en **estratos** (subgrupos con características comunes) y se selecciona una muestra de cada uno.
- Garantiza representación de todos los subgrupos relevantes.
- Muy usado en encuestas sociales y estudios de salud.

---
**Muestreo por conglomeración:** se divide la población en subgrupos y se seleccionan **grupos enteros**, no elementos individuales de cada grupo.
- Útil cuando la población está naturalmente agrupada: escuelas, barrios, empresas.
- A diferencia del estratificado, no se toman elementos de *todos* los grupos: se elige uno y se toma completo.

El **error de muestreo** es la diferencia entre un estadístico muestral y su parámetro correspondiente. No es un error humano: es una consecuencia inevitable de trabajar con muestras.

* Ningún método lo elimina por completo, pero un buen diseño lo controla.

---
<!-- _class: lead -->
# 02
# Distribución de Muestreo de Medias
## ¿Qué pasa si tomamos muchas muestras?
---
# La pregunta que cambia todo

Si tomamos una muestra y calculamos $\bar{x}$, obtenemos un número. Si tomamos otra muestra, obtenemos otro. Si tomamos *todas* las muestras posibles de tamaño $n$, obtenemos una **distribución de probabilidad**.

A esa distribución se la llama **distribución de muestreo de medias muestrales**: es la distribución de probabilidad de todas las medias posibles de un tamaño de muestra dado, con su probabilidad de ocurrencia asociada.

---
# Un ejemplo concreto

El estudio jurídico **Hoya & Asociados** tiene cinco socios. Cada semana informan las horas facturadas a sus clientes:

| Socio | Horas |
|:---:|:---:|
| Giordanino | 22 |
| Barnabá | 26 |
| Torres | 30 |
| Carrizo | 26 |
| Salgado | 22 |

¿Cuántas muestras de tamaño 2 son posibles?

$$C_5^2 = \frac{5!}{2!(5-2)!} = 10 \text{ muestras}$$

---
Organizando las 10 medias posibles se construye la distribución de muestreo:

| Media muestral | Frecuencia | Frecuencia relativa |
|:---:|:---:|:---:|
| 22 | 1 | 1/10 |
| 24 | 4 | 4/10 |
| 26 | 3 | 3/10 |
| 28 | 2 | 2/10 |

Esta tabla **es** la distribución de muestreo: a cada posible media le asignamos su probabilidad de ocurrencia.

---
# La propiedad fundamental

Calculamos la media de todas las medias muestrales:

$$\mu_{\bar{x}} = \frac{(22)(1) + (24)(4) + (26)(3) + (28)(2)}{10} = 25{,}2$$

La media poblacional vale:

$$\mu = \frac{22 + 26 + 30 + 26 + 22}{5} = 25{,}2$$

**Son exactamente iguales.** Y esto no es casualidad.

* Esta propiedad se cumple para cualquier población, independientemente de su tamaño.
* A medida que las muestras superan 30, la distribución cumple algo todavía más poderoso.

---
<!-- _class: lead -->
# 03
# Teorema del Límite Central
## El resultado más poderoso de la estadística.
---
# ¿Qué forma tiene esa distribución?

Ya sabemos que $\mu_{\bar{x}} = \mu$: en promedio, la media muestral no nos engaña.

Pero nos queda la pregunta más importante: ¿qué **forma** tiene esa distribución cuando las muestras son grandes?

La respuesta la da el **Teorema del Límite Central**.

---
# Teorema del Límite Central

Para una población con media $\mu$ y desvío estándar $\sigma$, la distribución de muestreo de las medias de todas las muestras posibles de tamaño $n$ tendrá una **distribución aproximadamente normal**, con media $\mu$ y desvío $\dfrac{\sigma}{\sqrt{n}}$, siempre que $n \geq 30$.

$$\boxed{\bar{x} \sim N\!\left(\mu_{\bar{x}} = \mu \;;\; \frac{\sigma}{\sqrt{n}}\right)}$$

* No importa qué forma tenga la distribución original de la población.
* Si $n \geq 30$, las medias muestrales **siempre** se distribuyen normalmente.
* (Esto es lo que nos permitirá construir intervalos de confianza en la Unidad 5)

---
# El error estándar

La cantidad $\sigma_{\bar{x}} = \dfrac{\sigma}{\sqrt{n}}$ tiene nombre propio: **error estándar del estimador**.

No es lo mismo que el desvío estándar poblacional $\sigma$:

* $\sigma$ mide la variabilidad de los **datos individuales** dentro de la población.
* $\sigma_{\bar{x}}$ mide la variabilidad de las **medias muestrales** entre sí.

A medida que $n$ crece, el error estándar **disminuye**: muestras más grandes producen estimaciones más concentradas alrededor de $\mu$.

* Intuitivamente: si medimos más, nuestra media tiene menos margen para alejarse del valor real.

---
<!-- _class: lead -->
# 04
# Estimaciones Puntuales
## Un primer paso hacia la inferencia.
---
# ¿Qué es una estimación puntual?

Una **estimación puntual** es un único valor calculado a partir de la muestra que se usa para aproximar un parámetro poblacional desconocido.

* $\bar{x}$ estima a $\mu$ → la media muestral como aproximación de la media poblacional.
* $s$ estima a $\sigma$ → el desvío muestral como aproximación del desvío poblacional.
* $\hat{p}$ estima a $P$ → la proporción muestral como aproximación de la proporción poblacional.

En este capítulo nos centramos en la **media poblacional**.

---
Una estimación puntual tiene una ventaja obvia: es simple y directa.

Pero tiene una limitación importante: **no dice cuán precisa es esa estimación**.

Si medimos 36 plantas y calculamos $\bar{x} = 1{,}6$ m, sabemos ese valor. Pero, ¿cuán cerca estamos de la media real? ¿Podría estar en 1,5 m? ¿En 1,9 m?

* La estimación puntual sola no responde eso.
* Para eso necesitamos los **intervalos de confianza**, que serán el tema de la Unidad 5.

---
# Tres caminos posibles

Ante la pregunta "¿cuál es la media de años de cursado en alumnos de Analítica?", hay tres opciones:

**Camino 1 — Censo:** conseguir la base completa y calcular $\mu$ directamente. Ideal, pero costoso y a veces imposible.

**Camino 2 — Estimación puntual:** tomar una muestra y calcular $\bar{x}$. Rápido y económico, pero sin medida de confianza.

**Camino 3 — Intervalo de confianza:** tomar una muestra y construir un rango que probablemente contenga a $\mu$, indicando el grado de confianza de esa afirmación.

* En este capítulo vimos los fundamentos del Camino 2. En la Unidad 5 construimos el Camino 3.

---
<!-- _class: lead -->
# Cierre
---
# Lo que construimos

**Parámetros y estimadores:**
La relación entre lo que existe en la población y lo que medimos en la muestra.

**Métodos de muestreo:**
Cómo seleccionar muestras representativas para que la inferencia sea legítima.

**Distribución de muestreo de medias:**
La distribución de probabilidad de todas las posibles $\bar{x}$ de un tamaño de muestra dado.

**Teorema del Límite Central:**
Por qué las medias muestrales tienden a la normalidad para $n \geq 30$, sin importar la forma de la población.

**Estimaciones puntuales:**
Un primer acercamiento a la inferencia, con sus alcances y sus límites.

---
# La lógica detrás de todo

La inferencia estadística no es magia.

Es una consecuencia directa del TLC: si sabemos que $\bar{x}$ se distribuye normalmente alrededor de $\mu$, podemos razonar en la dirección inversa y **usar $\bar{x}$ para construir afirmaciones cuantificables sobre $\mu$**.

Eso es exactamente lo que haremos en la Unidad 5.

---
# Preguntas guía

1. ¿Cuál es el fin de la estadística inferencial paramétrica y de qué se vale para ello?
2. ¿Cuáles son los estimadores y sus parámetros correspondientes?
3. ¿Qué diferencia hay entre la media poblacional y la media muestral?
4. ¿Cuál es la principal herramienta de Estadística I y qué parámetro estima?
5. ¿Cuáles son los tipos de muestreo aleatorio? ¿Qué ventajas tiene muestrear?
6. ¿Qué establece el Teorema del Límite Central?
7. ¿Cuál es la diferencia entre error estándar del estimador y desvío estándar poblacional?

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"Una muestra bien tomada vale más que un censo mal hecho."*
