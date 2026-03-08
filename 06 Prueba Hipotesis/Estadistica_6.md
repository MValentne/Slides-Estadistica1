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
# 06
# Prueba de Hipótesis
## De la muestra a la decisión.
---
En la unidad anterior aprendimos a *estimar* parámetros poblacionales a partir de muestras.

Ahora queremos ir un paso más allá: **tomar decisiones con esas estimaciones**.

* ¿Cambió algo después de una actualización?
* ¿El sistema funciona como prometió el fabricante?
* ¡La estadística puede responder eso, con un nivel de certeza medible!

---
<!-- _class: lead -->
# 01
# Inferencia y el Problema de los Datos Parciales
## Nunca tenemos todo. Aprendemos a trabajar con lo que hay.
---
Antes de probar hipótesis, hay que entender *por qué* trabajamos con muestras.

No es una limitación metodológica. Es la **realidad de los sistemas**.

* Los datos completos no existen. Existen logs, registros, muestras.
* Lo que calculamos sobre la muestra es una *estimación* del parámetro real.
* La inferencia es el puente que une ambos mundos.

---
# El Problema en Sistemas Reales

Como profesionales de sistemas, rara vez tenemos acceso a la totalidad de los datos.

* Analizar el tráfico de red *global* es imposible: trabajamos con **logs parciales**.
* Los tiempos de respuesta de un servidor no se pueden medir en *todas* las peticiones.

Por eso distinguimos siempre entre:

$$\text{Parámetro } (\mu,\ \sigma): \text{valor real de la } \textbf{población} \quad \longleftrightarrow \quad \text{Estadístico } (\bar{x},\ s): \text{valor calculado de la } \textbf{muestra}$$

---
# Teorema del Límite Central (TCL)

El **TCL** es el puente entre la muestra y la inferencia.

Si la muestra es suficientemente grande ($n > 30$), la distribución de medias muestrales se comporta como una **Normal**, aunque los datos originales no lo sean.

$$\bar{X} \sim N\!\left(\mu,\ \frac{\sigma}{\sqrt{n}}\right)$$

* Esto nos permite usar la distribución Z incluso cuando no sabemos cómo se distribuye la población.
* Es el fundamento que justifica todo lo que viene.

---
<!-- _class: lead -->
# 02
# Hipótesis, Errores y P-Valor
## Plantear bien la pregunta es la mitad de la respuesta.
---
Toda prueba de hipótesis es, en el fondo, una pregunta formal.

*¿Los datos que tengo son compatibles con lo que se afirma?*

* Primero hay que formular la pregunta correctamente.
* Después hay que saber qué significa equivocarse.
* Y finalmente, interpretar el resultado sin caer en errores clásicos.

---
# Hipótesis Nula e Hipótesis Alternativa

Toda prueba parte de **dos hipótesis opuestas**:

| | $H_0$ — Hipótesis Nula | $H_1$ — Hipótesis Alternativa |
|:---|:---|:---|
| **Rol** | El estado actual. Lo que se asume cierto. | Lo que queremos demostrar. |
| **Operadores** | $=,\ \leq,\ \geq$ | $\neq,\ <,\ >$ |

**Ejemplo:** una empresa afirma que su latencia media es 50ms.

$$H_0: \mu = 50 \qquad H_1: \mu \neq 50$$

---
## Una aclaración que no es menor

> **Nunca se dice "Acepto $H_0$".**

La prueba no demuestra que $H_0$ sea verdadera. Solo evalúa si hay *evidencia suficiente* para rechazarla.

Si la evidencia es insuficiente, la conclusión correcta es:

$$\boxed{\text{"No se rechaza } H_0\text{"}}$$

* Es una distinción que importa tanto en la academia como frente a un juzgado.

---
# El P-Valor

El **p-valor** es la probabilidad de obtener un resultado tan extremo como el observado, *asumiendo que $H_0$ es verdadera*.

$$\text{p-valor} < \alpha \quad \Rightarrow \quad \textbf{RECHAZO } H_0$$
$$\text{p-valor} > \alpha \quad \Rightarrow \quad \textbf{NO RECHAZO } H_0$$

Donde $\alpha$ es el **nivel de significancia** elegido previamente (típicamente 0.05 o 0.01).

* Un p-valor pequeño dice: "esto sería muy raro si $H_0$ fuera cierta". La evidencia habla.

---
# ¿Cómo se calcula el P-Valor?

El p-valor se obtiene a partir del **estadístico calculado** ($Z_{calc}$ o $T_{calc}$) y el **tipo de prueba**:

| Tipo de prueba | Fórmula del p-valor |
|:---|:---|
| Bilateral ($H_1: \mu \neq \mu_0$) | $p = 2 \cdot P(Z > \|Z_{calc}\|)$ |
| Unilateral derecha ($H_1: \mu > \mu_0$) | $p = P(Z > Z_{calc})$ |
| Unilateral izquierda ($H_1: \mu < \mu_0$) | $p = P(Z < Z_{calc})$ |

Donde $P(Z > z)$ es el **área bajo la curva normal estándar** a la derecha de $z$, también escrita como $1 - \Phi(z)$, siendo $\Phi$ la función de distribución acumulada.

---
# El P-Valor: Interpretación Geométrica

Para una prueba **bilateral** con $Z_{calc} = 3.16$:

$$p = 2 \cdot P(Z > 3.16) = 2 \cdot (1 - \Phi(3.16))$$

De tabla: $\Phi(3.16) \approx 0.9992$

$$p = 2 \cdot (1 - 0.9992) = 2 \cdot 0.0008 = \mathbf{0.0016}$$

El área sombreada (la probabilidad de observar algo tan extremo) representa el p-valor.
Como $0.0016 < 0.05 = \alpha$, **se rechaza $H_0$**.

> El p-valor no es la probabilidad de que $H_0$ sea falsa. Es la probabilidad de *ver estos datos* si $H_0$ fuera verdadera.

---
# Demostración Simple: ¿La latencia cambió?

Retomamos el ejemplo del servidor: $\bar{x} = 55\text{ms}$, $\mu_0 = 50$, $s = 10$, $n = 40$.

**Paso 1 — Calcular el estadístico:**

$$Z_{calc} = \frac{55 - 50}{10/\sqrt{40}} = \frac{5}{1.58} = 3.16$$

**Paso 2 — Calcular el p-valor** (prueba bilateral):

$$p = 2 \cdot P(Z > 3.16) = 2 \cdot (1 - 0.9992) = 0.0016$$

---

**Paso 3 — Decidir:**

$$p = 0.0016 < \alpha = 0.05 \quad \Rightarrow \quad \textbf{Se rechaza } H_0$$

**Conclusión:** La probabilidad de observar una diferencia tan grande por puro azar es del 0,16%. La evidencia es contundente.

---
# Los dos errores posibles

Al decidir sobre $H_0$, podemos equivocarnos de dos maneras distintas:

| | $H_0$ es verdadera | $H_0$ es falsa |
|:---|:---:|:---:|
| **Rechazo $H_0$** | Error Tipo I ($\alpha$) | Decisión correcta |
| **No rechazo $H_0$** | Decisión correcta | Error Tipo II ($\beta$) |

* **Error Tipo I:** rechazar $H_0$ cuando en realidad es verdadera. La probabilidad de cometerlo es exactamente $\alpha$.
* **Error Tipo II:** no rechazar $H_0$ cuando en realidad es falsa. Su probabilidad es $\beta$.

---

Elegir $\alpha$ pequeño reduce el Error Tipo I, pero aumenta el riesgo del Tipo II. Siempre hay un trade-off.

---
<!-- _class: lead -->
# 03
# Criterio de Selección: ¿Z o T?
## La herramienta depende de lo que sabemos.
---
Ya sabemos plantear hipótesis. Ahora hay que elegir *con qué herramienta* las probamos.

No es una decisión arbitraria. Depende de **lo que conocemos** del problema.

* ¿Tenemos el desvío real de la población, o solo el de la muestra?
* ¿Cuántos datos tenemos?
* La respuesta a esas dos preguntas determina todo lo que sigue.

---
# ¿Cuándo usar cada distribución?

Dos preguntas, en orden:

**① ¿Conozco $\sigma$ poblacional?**
→ Sí: **uso Z**, sin importar el tamaño de la muestra.
→ No: paso a la segunda pregunta.

**② ¿$n \geq 30$?**
→ Sí: **uso Z** igualmente, gracias al TCL.
→ No ($n < 30$): **uso T-Student**.

* La T-Student requiere además asumir que la población de origen es **aproximadamente normal**.
* Los grados de libertad se calculan como $gl = n - 1$.

---
<!-- _class: lead -->
# Muestras Grandes
## $n \geq 30$: el TCL nos respalda.
---
Con muestras grandes, el TCL garantiza que la distribución de medias es Normal.

Eso nos da permiso de usar **Z**, aunque no conozcamos $\sigma$ de la población.

* El estadístico calculado se compara contra un límite crítico fijo.
* Si lo supera, la diferencia es demasiado grande para ser solo azar.

---
# Estadístico de Prueba Z

$$Z_{calc} = \frac{\bar{x} - \mu_0}{\sigma / \sqrt{n}}$$

Si $Z_{calc}$ cae fuera de los límites críticos, hay evidencia para rechazar $H_0$.

Los límites críticos dependen del tipo de prueba y del nivel $\alpha$:

| Tipo de prueba | $\alpha = 0.05$ | $\alpha = 0.01$ |
|:---|:---:|:---:|
| Bilateral ($H_1: \mu \neq$) | $\pm 1.96$ | $\pm 2.58$ |
| Unilateral derecha ($H_1: \mu >$) | $1.645$ | $2.33$ |
| Unilateral izquierda ($H_1: \mu <$) | $-1.645$ | $-2.33$ |

---
## Ejemplo: Latencia de un servidor

Una empresa afirma que su latencia media es 50ms. Una auditoría toma $n = 40$ peticiones y obtiene $\bar{x} = 55\text{ms}$ con $s = 10\text{ms}$. ¿Cambió la latencia? ($\alpha = 0.05$)

**Hipótesis:** $H_0: \mu = 50$ vs $H_1: \mu \neq 50$ → Bilateral. $n = 40 > 30$, usamos Z.

**Límites críticos:** $\pm 1.96$

$$Z = \frac{55 - 50}{10/\sqrt{40}} = \frac{5}{1.58} = \mathbf{3.16}$$

**Decisión:** $3.16 > 1.96$ → Cae en zona de rechazo.

**Conclusión:** Existe evidencia suficiente para afirmar que la latencia ha cambiado.

---
## Ejemplo: Optimización de un script

Un script tarda históricamente 200ms. Tras refactorización, $n = 35$ ejecuciones dan $\bar{x} = 190\text{ms}$ y $s = 25\text{ms}$. ¿Fue efectiva la mejora? ($\alpha = 0.05$)

**Hipótesis:** $H_0: \mu \geq 200$ vs $H_1: \mu < 200$ → Unilateral izquierda. Usamos Z.

**Límite crítico:** $-1.645$

$$Z = \frac{190 - 200}{25/\sqrt{35}} = \frac{-10}{4.22} = \mathbf{-2.36}$$

**Decisión:** $-2.36 < -1.645$ → Cae en zona de rechazo.

**Conclusión:** La optimización fue efectiva. El tiempo bajó significativamente.

---
## Ejemplo: Alertas de un IDS

Un IDS reporta en promedio 5 alertas diarias. Tras una actualización, se monitorean 50 días: $\bar{x} = 5.2$ alertas con $s = 1.5$. ¿Cambió el promedio? ($\alpha = 0.01$)

**Hipótesis:** $H_0: \mu = 5$ vs $H_1: \mu \neq 5$ → Bilateral. $n = 50$, usamos Z.

**Límites críticos:** $\pm 2.58$

$$Z = \frac{5.2 - 5}{1.5/\sqrt{50}} = \frac{0.2}{0.21} = \mathbf{0.94}$$

**Decisión:** $0.94$ cae en zona central.

**Conclusión:** No se rechaza $H_0$. La variación puede ser azarosa.

---
## Ejemplo: Nueva interfaz de e-commerce

Ticket promedio histórico: \$15.000. Nueva interfaz, $n = 100$ usuarios: $\bar{x} = \$15.800$, $s = \$3.000$. ¿Aumentaron las ventas? ($\alpha = 0.05$)

**Hipótesis:** $H_0: \mu \leq 15000$ vs $H_1: \mu > 15000$ → Unilateral derecha. Usamos Z.

**Límite crítico:** $1.645$

$$Z = \frac{15800 - 15000}{3000/\sqrt{100}} = \frac{800}{300} = \mathbf{2.67}$$

**Decisión:** $2.67 > 1.645$ → Cae en zona de rechazo.

**Conclusión:** Las ventas aumentaron significativamente.

---
## Retomando...

Cuatro situaciones distintas, cuatro veces el mismo proceso.

* Bilateral cuando no sabemos hacia dónde puede ir el cambio.
* Unilateral cuando la pregunta tiene dirección: ¿mejoró? ¿empeoró?
* La conclusión siempre cierra con palabras, no solo con números.

Lo que sigue es el mismo procedimiento, pero con una herramienta diferente.

---
<!-- _class: lead -->
# Muestras Pequeñas
## $n < 30$: la incertidumbre es mayor.
---
Con pocos datos, el TCL ya no aplica.

La distribución Z subestima la variabilidad real de la muestra.

* Necesitamos una herramienta que reconozca esa incertidumbre adicional.
* La **T-Student** tiene colas más anchas: es más conservadora, más honesta.
* Cuantos más grados de libertad, más se parece a la Z.

---
# La distribución T-Student

La **T-Student** reconoce que con muestras chicas, la incertidumbre es mayor.

$$T = \frac{\bar{x} - \mu_0}{S / \sqrt{n}} \qquad \text{con } gl = n - 1 \text{ grados de libertad}$$

* El valor crítico no es fijo: depende de $gl$ y se consulta en la **tabla T**.
* A medida que $n$ crece, los valores T se acercan a los valores Z.

---
## Ejemplo: Temperatura de una GPU

Un fabricante afirma que su placa opera a 85°C. Un reviewer prueba $n = 10$ placas y obtiene $\bar{x} = 88°C$ con $s = 3°C$. ¿Calienta más de lo prometido? ($\alpha = 0.05$)

**Hipótesis:** $H_0: \mu \leq 85$ vs $H_1: \mu > 85$ → Unilateral derecha. $n = 10$, $gl = 9$.

**Límite crítico** (tabla T, $\alpha = 0.05$, 1 cola, 9 gl): $T_{crit} = 1.833$

$$T = \frac{88 - 85}{3/\sqrt{10}} = \frac{3}{0.948} = \mathbf{3.16}$$

**Decisión:** $3.16 > 1.833$ → Zona de rechazo.

**Conclusión:** Hay evidencia para afirmar que las placas calientan significativamente más de 85°C.

---
## Ejemplo: Tiempo de registro (UX)

Una tarea de registro tarda 60 segundos. Se rediseña el formulario y se prueba con $n = 16$ beta testers: $\bar{x} = 58s$, $s = 5s$. ¿Se redujo el tiempo? ($\alpha = 0.01$)

**Hipótesis:** $H_0: \mu \geq 60$ vs $H_1: \mu < 60$ → Unilateral izquierda. $n = 16$, $gl = 15$.

**Límite crítico** (tabla T, $\alpha = 0.01$, 1 cola, 15 gl): $T_{crit} = -2.602$

$$T = \frac{58 - 60}{5/\sqrt{16}} = \frac{-2}{1.25} = \mathbf{-1.60}$$

**Decisión:** $-1.60$ no es menor que $-2.602$ → Zona de no rechazo.

**Conclusión:** No se rechaza $H_0$. Con una muestra tan pequeña y $\alpha = 0.01$, no hay evidencia estadística suficiente para confirmar la mejora.

---
<!-- _class: lead -->
# En resumen...
## El procedimiento completo.
---
# Los tres pasos de toda prueba

Toda prueba de hipótesis, sin importar el contexto, sigue la misma estructura:

**1. Plantear las hipótesis**
Definir $H_0$ y $H_1$, identificar si la prueba es bilateral o unilateral.

**2. Determinar la zona de rechazo**
Elegir Z o T según los datos disponibles. Buscar el valor crítico según $\alpha$.

**3. Calcular el estadístico y decidir**
Comparar el estadístico calculado contra el crítico. Concluir con precisión.

---
# Guía de selección rápida

| Situación | Distribución | Estadístico |
|:---|:---:|:---:|
| Conocemos $\sigma$, cualquier $n$ | Z | $Z = \dfrac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$ |
| $n \geq 30$, usamos $S$ | Z (por TCL) | $Z = \dfrac{\bar{x} - \mu_0}{S/\sqrt{n}}$ |
| $n < 30$, desconocemos $\sigma$ | T-Student | $T = \dfrac{\bar{x} - \mu_0}{S/\sqrt{n}}$ |

---
<!-- _class: lead -->
# Cierre

---
# Lo que aprendimos

**Inferencia estadística:**
Tomar decisiones sobre una población a partir de una muestra, con un nivel de confianza medible.

**Hipótesis nula y alternativa:**
$H_0$ es el estado actual; $H_1$ es lo que queremos demostrar. Nunca "aceptamos" $H_0$, solo dejamos de rechazarla.

**Z y T-Student:**
Dos herramientas para el mismo fin. La elección depende del tamaño de la muestra y del conocimiento de $\sigma$.

**El p-valor:**
La traducción numérica de cuán compatible es la muestra con $H_0$.

---
# Las pruebas como argumento formal

**Una prueba de hipótesis no es solo estadística.**

Es una forma de argumentar con evidencia. De decir: *"observé esto, y la probabilidad de que sea solo azar es menor al 5%"*.

Ese argumento es válido en un paper, en un informe técnico, y también frente a un juez.

---
# Reflexión final

**Un resultado estadísticamente significativo no siempre es importante.**

**Y un resultado importante no siempre es estadísticamente significativo.**

El nivel $\alpha$, el tamaño de la muestra, y el contexto del problema son parte de la decisión, no solo el número que sale al final.

En estadística no eliminamos la incertidumbre. **Aprendemos a cuantificarla y a decidir con ella.**

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"El experimento es el único juez de la verdad científica."*
— Richard Feynman
