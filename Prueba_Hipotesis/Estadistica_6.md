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

> ⚠️ **Nunca se dice "Acepto $H_0$".**

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
<!-- _class: lead -->
# 03
# Criterio de Selección: ¿Z o T?
## La herramienta depende de lo que sabemos.
---
# ¿Cuándo usar cada distribución?

La elección entre Z y T depende de dos factores: **¿conocemos $\sigma$?** y **¿qué tan grande es la muestra?**

| Condición | Distribución |
|:---|:---:|
| Conocemos $\sigma$ poblacional | **Z** |
| $n \geq 30$ (por TCL) | **Z** |
| Desconocemos $\sigma$, usamos $S$, y $n < 30$ | **T-Student** |

* La T-Student requiere además asumir que la población de origen es **aproximadamente normal**.
* Los grados de libertad se calculan como $gl = n - 1$.

---
<!-- _class: lead -->
# Bloque A
# Muestras Grandes
## Cuando $n \geq 30$: usamos Z.
---
El estadístico Z mide cuántos errores estándar se aleja la media muestral del valor hipotético:

$$Z = \frac{\bar{x} - \mu_0}{\sigma / \sqrt{n}}$$

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
<!-- _class: lead -->
# Bloque B
# Muestras Pequeñas
## Cuando $n < 30$: usamos T-Student.
---
# La distribución T-Student

Cuando la muestra es pequeña y no conocemos $\sigma$, la distribución Z ya no es confiable.

La **T-Student** tiene una forma similar a la Normal pero con colas más anchas, reconociendo la mayor incertidumbre de muestras chicas.

$$T = \frac{\bar{x} - \mu_0}{S / \sqrt{n}} \qquad \text{con } gl = n - 1 \text{ grados de libertad}$$

* A medida que $n$ crece, la T se parece cada vez más a la Z.
* El valor crítico se busca en la **tabla T** con los grados de libertad correspondientes.

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

*"En Dios confiamos. Todos los demás deben traer datos."*
— W. Edwards Deming
