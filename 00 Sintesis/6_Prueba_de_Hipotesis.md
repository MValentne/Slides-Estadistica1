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
# Prueba de Hipótesis
## De la muestra a la decisión

---

# ¿Qué es una prueba de hipótesis?

Una forma de **tomar decisiones sobre parámetros poblacionales** a partir de una muestra, con un nivel de certeza medible.

*¿Cambió algo tras una actualización? ¿El sistema funciona como prometió el fabricante?*

Toda prueba parte de dos hipótesis opuestas:

| | $H_0$ — Hipótesis Nula | $H_1$ — Hipótesis Alternativa |
|:---|:---|:---|
| **Rol** | Estado actual. Lo que se asume cierto. | Lo que queremos demostrar. |
| **Operadores** | $=,\ \leq,\ \geq$ | $\neq,\ <,\ >$ |

---

# Una distinción que no es menor

> **Nunca se dice "Acepto $H_0$".**

La prueba solo evalúa si hay *evidencia suficiente* para rechazarla.

$$\boxed{\text{Conclusión correcta cuando la evidencia es insuficiente: "No se rechaza } H_0\text{"}}$$

Esta distinción importa tanto en la academia como **frente a un juzgado**.

---

# El P-Valor

Probabilidad de obtener un resultado tan extremo como el observado, **asumiendo que $H_0$ es verdadera**.

$$\text{p-valor} < \alpha \;\Rightarrow\; \textbf{RECHAZO } H_0 \qquad \text{p-valor} \geq \alpha \;\Rightarrow\; \textbf{NO RECHAZO } H_0$$

| Tipo de prueba | P-valor |
|:---|:---|
| Bilateral ($H_1: \mu \neq \mu_0$) | $p = 2 \cdot P(Z > \|Z_{calc}\|)$ |
| Unilateral derecha ($H_1: \mu > \mu_0$) | $p = P(Z > Z_{calc})$ |
| Unilateral izquierda ($H_1: \mu < \mu_0$) | $p = P(Z < Z_{calc})$ |

> El p-valor no es la probabilidad de que $H_0$ sea falsa — es la probabilidad de *ver estos datos* si $H_0$ fuera verdadera.

---

# Los dos errores posibles

| | $H_0$ verdadera | $H_0$ falsa |
|:---|:---:|:---:|
| **Rechazo $H_0$** | Error Tipo I — prob. $\alpha$ | ✓ Decisión correcta |
| **No rechazo $H_0$** | ✓ Decisión correcta | Error Tipo II — prob. $\beta$ |

Reducir $\alpha$ disminuye el Error Tipo I pero aumenta el riesgo del Tipo II. Siempre hay un **trade-off**.

---

<!-- _class: lead -->
# ¿Z o T de Student?

---

# Criterio de selección

**① ¿Conozco $\sigma$ poblacional?**
→ Sí → **uso Z**, sin importar $n$.

**② ¿$n \geq 30$?**
→ Sí → **uso Z** (TCL garantiza normalidad).
→ No → **uso T-Student** con $gl = n - 1$.

| Situación | Distribución | Estadístico |
|:---|:---:|:---:|
| $\sigma$ conocida, cualquier $n$ | $Z$ | $Z = \dfrac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$ |
| $n \geq 30$, $\sigma$ desconocida | $Z$ (TCL) | $Z = \dfrac{\bar{x} - \mu_0}{s/\sqrt{n}}$ |
| $n < 30$, $\sigma$ desconocida | $T$ | $T = \dfrac{\bar{x} - \mu_0}{s/\sqrt{n}}$ |

---

# Valores críticos — distribución Z

| Tipo de prueba | $\alpha = 0{,}05$ | $\alpha = 0{,}01$ |
|:---|:---:|:---:|
| Bilateral ($H_1: \mu \neq$) | $\pm 1{,}96$ | $\pm 2{,}58$ |
| Unilateral derecha ($H_1: \mu >$) | $1{,}645$ | $2{,}33$ |
| Unilateral izquierda ($H_1: \mu <$) | $-1{,}645$ | $-2{,}33$ |

---

<!-- _class: lead -->
# Ejemplos con distribución $Z$

---

# Ejemplo 1: Latencia de un servidor

$\mu_0 = 50\text{ms}$, $\bar{x} = 55\text{ms}$, $s = 10\text{ms}$, $n = 40$, $\alpha = 0{,}05$

$H_0: \mu = 50$ vs $H_1: \mu \neq 50$ → **Bilateral**. Límites: $\pm 1{,}96$

$$Z = \frac{55 - 50}{10/\sqrt{40}} = \frac{5}{1{,}58} = \mathbf{3{,}16} \quad \Rightarrow \quad p = 2(1-\Phi(3{,}16)) = 0{,}0016$$

$3{,}16 > 1{,}96$ y $p = 0{,}0016 < 0{,}05$ → **Se rechaza $H_0$**

> Existe evidencia de que la latencia ha cambiado.

---

# Ejemplo 2: Optimización de un script

$\mu_0 = 200\text{ms}$, $\bar{x} = 190\text{ms}$, $s = 25\text{ms}$, $n = 35$, $\alpha = 0{,}05$

$H_0: \mu \geq 200$ vs $H_1: \mu < 200$ → **Unilateral izquierda**. Límite: $-1{,}645$

$$Z = \frac{190 - 200}{25/\sqrt{35}} = \frac{-10}{4{,}22} = \mathbf{-2{,}36}$$

$-2{,}36 < -1{,}645$ → **Se rechaza $H_0$**

> La optimización fue efectiva. El tiempo bajó significativamente.

---

# Ejemplo 3: Alertas de un IDS

$\mu_0 = 5$ alertas/día, $\bar{x} = 5{,}2$, $s = 1{,}5$, $n = 50$, $\alpha = 0{,}01$

$H_0: \mu = 5$ vs $H_1: \mu \neq 5$ → **Bilateral**. Límites: $\pm 2{,}58$

$$Z = \frac{5{,}2 - 5}{1{,}5/\sqrt{50}} = \frac{0{,}2}{0{,}21} = \mathbf{0{,}94}$$

$0{,}94$ cae en zona central → **No se rechaza $H_0$**

> La variación puede ser azarosa. Sin evidencia de cambio.

---

<!-- _class: lead -->
# Ejemplos con T de Student

---

# Ejemplo 4: Temperatura de una GPU

$\mu_0 = 85°C$, $\bar{x} = 88°C$, $s = 3°C$, $n = 10$, $gl = 9$, $\alpha = 0{,}05$

$H_0: \mu \leq 85$ vs $H_1: \mu > 85$ → **Unilateral derecha**. $T_{crit} = 1{,}833$

$$T = \frac{88 - 85}{3/\sqrt{10}} = \frac{3}{0{,}948} = \mathbf{3{,}16}$$

$3{,}16 > 1{,}833$ → **Se rechaza $H_0$**

> Las placas calientan significativamente más de lo prometido.

---

# Ejemplo 5: Tiempo de registro (UX)

$\mu_0 = 60\text{s}$, $\bar{x} = 58\text{s}$, $s = 5\text{s}$, $n = 16$, $gl = 15$, $\alpha = 0{,}01$

$H_0: \mu \geq 60$ vs $H_1: \mu < 60$ → **Unilateral izquierda**. $T_{crit} = -2{,}602$

$$T = \frac{58 - 60}{5/\sqrt{16}} = \frac{-2}{1{,}25} = \mathbf{-1{,}60}$$

$-1{,}60 > -2{,}602$ → **No se rechaza $H_0$**

> Con muestra pequeña y $\alpha = 0{,}01$, la evidencia es insuficiente para confirmar la mejora.

---

<!-- _class: lead -->
# Cierre

---

# Los tres pasos de toda prueba

**1. Plantear las hipótesis**
Definir $H_0$ y $H_1$ · Identificar si es bilateral o unilateral

**2. Determinar la zona de rechazo**
Elegir $Z$ o $T$ · Buscar el valor crítico según $\alpha$ y $gl$

**3. Calcular el estadístico y decidir**
Comparar con el valor crítico (o calcular el p-valor) · Concluir con palabras

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **$H_0$ y $H_1$** | Formalizar la pregunta estadística |
| **P-valor** | Cuantificar la compatibilidad con $H_0$ |
| **Errores Tipo I y II** | Entender las consecuencias de equivocarse |
| **Distribución $Z$** | Muestras grandes o $\sigma$ conocida |
| **T de Student** | Muestras pequeñas, $\sigma$ desconocida |

---

# Reflexión final

**Un resultado estadísticamente significativo no siempre es importante.**
**Y un resultado importante no siempre es estadísticamente significativo.**

El nivel $\alpha$, el tamaño de muestra y el contexto son parte de la decisión, no solo el número final.

> *"El experimento es el único juez de la verdad científica."*
> — Richard Feynman

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
