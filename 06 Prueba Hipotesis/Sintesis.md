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
* La estadística puede responder eso, con un **nivel de certeza medible**.

---
<!-- _class: lead -->
# 01
# Inferencia y Datos Parciales
## Nunca tenemos todo. Aprendemos a trabajar con lo que hay.
---
# Inferencia y el TCL

Los datos completos no existen. Trabajamos con muestras — logs, registros, mediciones parciales.

$$\text{Parámetro } (\mu,\ \sigma): \textbf{población} \quad \longleftrightarrow \quad \text{Estadístico } (\bar{x},\ s): \textbf{muestra}$$

La **inferencia** es el puente. Y su fundamento es el **Teorema del Límite Central**:

> Si $n > 30$, la distribución de medias muestrales se comporta como una Normal, aunque los datos originales no lo sean.

$$\bar{X} \sim N\!\left(\mu,\ \frac{\sigma}{\sqrt{n}}\right)$$

---
<!-- _class: lead -->
# 02
# Hipótesis, Errores y P-Valor
## Plantear bien la pregunta es la mitad de la respuesta.
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

$$\text{p-valor} < \alpha \quad \Rightarrow \quad \textbf{RECHAZO } H_0 \qquad \text{p-valor} > \alpha \quad \Rightarrow \quad \textbf{NO RECHAZO } H_0$$

Donde $\alpha$ es el **nivel de significancia** elegido previamente ($0.05$ o $0.01$).

* **Bilateral** ($H_1: \mu \neq \mu_0$): $\quad p = 2 \cdot P(Z > |Z_{calc}|)$
* **Unilateral derecha** ($H_1: \mu > \mu_0$): $\quad p = P(Z > Z_{calc})$
* **Unilateral izquierda** ($H_1: \mu < \mu_0$): $\quad p = P(Z < Z_{calc})$

> El p-valor no es la probabilidad de que $H_0$ sea falsa. Es la probabilidad de *ver estos datos* si $H_0$ fuera verdadera.

---
# Los Dos Errores Posibles

Al decidir sobre $H_0$, podemos equivocarnos de dos maneras distintas:

| | $H_0$ es verdadera | $H_0$ es falsa |
|:---|:---:|:---:|
| **Rechazo $H_0$** | Error Tipo I ($\alpha$) | Decisión correcta |
| **No rechazo $H_0$** | Decisión correcta | Error Tipo II ($\beta$) |

* **Error Tipo I ($\alpha$):** rechazar $H_0$ cuando en realidad es verdadera.
* **Error Tipo II ($\beta$):** no rechazar $H_0$ cuando en realidad es falsa.

Reducir $\alpha$ disminuye el Error Tipo I, pero aumenta el riesgo del Tipo II. Siempre hay un **trade-off**.

---
<!-- _class: lead -->
# 03
# Criterio de Selección: ¿Z o T?
## La herramienta depende de lo que sabemos.
---
# ¿Cuándo usar cada distribución?

Dos preguntas, en orden:

**① ¿Conozco $\sigma$ poblacional?**
→ Sí: **uso Z**, sin importar el tamaño de la muestra.
→ No: paso a la segunda pregunta.

**② ¿$n \geq 30$?**
→ Sí: **uso Z** igualmente, gracias al TCL.
→ No ($n < 30$): **uso T-Student**.

* La T-Student requiere además asumir que la población es **aproximadamente normal**.
* Los grados de libertad se calculan como $gl = n - 1$.

---
# Estadístico de Prueba Z

$$Z_{calc} = \frac{\bar{x} - \mu_0}{\sigma / \sqrt{n}}$$

Los límites críticos dependen del tipo de prueba y del nivel $\alpha$:

| Tipo de prueba | $\alpha = 0.05$ | $\alpha = 0.01$ |
|:---|:---:|:---:|
| Bilateral ($H_1: \mu \neq$) | $\pm 1.96$ | $\pm 2.58$ |
| Unilateral derecha ($H_1: \mu >$) | $1.645$ | $2.33$ |
| Unilateral izquierda ($H_1: \mu <$) | $-1.645$ | $-2.33$ |

---
## Ejemplo: Latencia de un servidor

Una empresa afirma que su latencia media es 50ms. Auditoría: $n = 40$, $\bar{x} = 55\text{ms}$, $s = 10\text{ms}$. ¿Cambió? ($\alpha = 0.05$)

**Hipótesis:** $H_0: \mu = 50$ vs $H_1: \mu \neq 50$ — Bilateral. Usamos Z.

$$Z = \frac{55 - 50}{10/\sqrt{40}} = \frac{5}{1.58} = \mathbf{3.16} \quad > \quad 1.96$$

$p = 2 \cdot (1 - \Phi(3.16)) = 2 \cdot 0.0008 = \mathbf{0.0016} < 0.05$

**Conclusión:** Se rechaza $H_0$. La probabilidad de observar esta diferencia por azar es del 0,16%. La evidencia es contundente.

---
# La Distribución T-Student

Con pocos datos, el TCL ya no aplica. La T-Student reconoce esa incertidumbre adicional con **colas más anchas**.

$$T = \frac{\bar{x} - \mu_0}{S / \sqrt{n}} \qquad \text{con } gl = n - 1 \text{ grados de libertad}$$

* El valor crítico no es fijo: depende de $gl$ y se consulta en la **tabla T**.
* A medida que $n$ crece, los valores T convergen hacia los valores Z.

---
## Ejemplo: Temperatura de una GPU

Fabricante afirma 85°C. Reviewer prueba $n = 10$ placas: $\bar{x} = 88°C$, $s = 3°C$. ¿Calienta más? ($\alpha = 0.05$)

**Hipótesis:** $H_0: \mu \leq 85$ vs $H_1: \mu > 85$ — Unilateral derecha. $gl = 9$.

**Valor crítico** (tabla T, $\alpha = 0.05$, 1 cola, 9 gl): $T_{crit} = 1.833$

$$T = \frac{88 - 85}{3/\sqrt{10}} = \frac{3}{0.948} = \mathbf{3.16} \quad > \quad 1.833$$

**Conclusión:** Se rechaza $H_0$. Hay evidencia de que las placas calientan significativamente más de lo prometido.

---
<!-- _class: lead -->
# En resumen...
## El procedimiento completo.
---
# Guía de Selección Rápida

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

**Hipótesis:** $H_0$ es el estado actual; $H_1$ es lo que queremos demostrar. Nunca "aceptamos" $H_0$, solo dejamos de rechazarla.

**Errores:** Tipo I ($\alpha$) — rechazar cuando no debía. Tipo II ($\beta$) — no rechazar cuando debía. Reducir uno aumenta el otro.

**Z y T-Student:** dos herramientas para el mismo fin. La elección depende del tamaño de la muestra y del conocimiento de $\sigma$.

**El p-valor:** la traducción numérica de cuán compatible es la muestra con $H_0$.

> Un resultado estadísticamente significativo no siempre es importante. Y un resultado importante no siempre es estadísticamente significativo.

---
# Las Pruebas como Argumento Formal

**Una prueba de hipótesis no es solo estadística.**

Es una forma de argumentar con evidencia. De decir:

> *"Observé esto, y la probabilidad de que sea solo azar es menor al 5%."*

Ese argumento es válido en un paper, en un informe técnico, y también **frente a un juez**.

El nivel $\alpha$, el tamaño de la muestra y el contexto son parte de la decisión — no solo el número que sale al final.

En estadística no eliminamos la incertidumbre. **Aprendemos a cuantificarla y a decidir con ella.**

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"El experimento es el único juez de la verdad científica."*
— Richard Feynman