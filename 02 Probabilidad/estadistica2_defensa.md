---
marp: true
theme: academic
math: katex
paginate: true

---
# Estadística I
# UNM - FCEQyN - 2025
## Valentino Mende
### Unidad II

---
<!-- _class: lead -->
# Introducción
# Combinatoria y Probabilidad
## Del azar a los números

---
# ¿Por qué combinatoria primero?

La probabilidad asigna un número a cada posible resultado de un experimento aleatorio.

* Para eso, necesitamos saber **cuántos resultados posibles existen**.
* Y cuántos de ellos nos **favorecen**.
* Aquí entra la **combinatoria**.

> *Nació de cuadrados mágicos, dados y huesos de animal. Hoy es el fundamento de la IA y la seguridad informática.*

---
<!-- _class: lead -->
# 00
# Técnicas de Conteo
## Antes de calcular, hay que saber contar.

---
# Factorial y el Principio de Multiplicación

$$n! = n \cdot (n-1) \cdot (n-2) \cdots 1 \qquad \text{con } 0! = 1$$

**Principio de multiplicación:** si un suceso ocurre de $m$ formas y luego otro de $n$ formas, el total es $m \times n$.

**Ejemplo:** 5 personas entrando de a una a un consultorio:

$$5! = 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 120 \text{ ordenamientos posibles}$$

---
# Variaciones y Permutaciones

**Variaciones** (orden importa, sin repetición):

$$V_m^n = \frac{m!}{(m-n)!}$$

**Permutaciones** (todos los elementos, orden importa):

$$P_n = n! \qquad \text{Circulares: } PC_n = (n-1)!$$

**Ejemplo:** 5 personas en 3 sillas → $V_5^3 = \frac{5!}{2!} = 60$

---
# Variaciones con Repetición

Cuando **sí se pueden repetir** los elementos y el orden importa:

$$VR_m^n = m^n$$

**Ejemplo clásico: las patentes argentinas (ABC 123)**

* 3 letras: $27^3 = 19.683$ opciones
* 3 dígitos: $10^3 = 1.000$ opciones

$$T = 19.683 \times 1.000 = \mathbf{19.683.000} \text{ autos patentados}$$

---
# Combinaciones

**No importa el orden, sin repetición:**

$$C_m^n = \frac{m!}{n!(m-n)!}$$

**Con repetición:**

$$CR_m^n = \frac{(m+n-1)!}{n!(m-1)!}$$

**Ejemplo:** Clase de 10 niños y 6 niñas. ¿De cuántas formas se elige un comité de 3?

$$C_{16}^3 = \frac{16!}{3! \cdot 13!} = 560 \text{ combinaciones posibles}$$

---
# Resumen: ¿cuál usar?

| Técnica | Orden | Repetición | Fórmula |
|:---:|:---:|:---:|:---:|
| Variaciones | ✓ | ✗ | $\frac{m!}{(m-n)!}$ |
| Var. con Rep. | ✓ | ✓ | $m^n$ |
| Permutaciones | ✓ | ✗ | $n!$ |
| Perm. Circular | ✓ | ✗ | $(n-1)!$ |
| Combinaciones | ✗ | ✗ | $\frac{m!}{n!(m-n)!}$ |
| Comb. con Rep. | ✗ | ✓ | $\frac{(m+n-1)!}{n!(m-1)!}$ |

---
<!-- _class: lead -->
# 01
# Introducción a la Probabilidad
## Ponerle número al azar.

---
# ¿Qué es la probabilidad?

Un número entre **0 y 1** que indica las posibilidades de que ocurra un suceso en un experimento aleatorio.

- **0** → imposible.
- **1** → certeza.

**Probabilidad objetiva: dos enfoques**

* **A priori:** se calcula antes de realizar ensayos. Al lanzar un dado: $P(\text{valor}) = \frac{1}{6}$.
* **A posteriori:** se basa en datos registrados. *La prevalencia de diabetes en Misiones es del 15%.*

---
# Espacio Muestral y Sucesos

El **espacio muestral** $E$ (o $\Omega$) es el conjunto de todos los resultados posibles.

Un **suceso** es un subconjunto del espacio muestral.

**Tipos de sucesos clave:**
- **Seguro** → contiene todos los resultados posibles.
- **Imposible ($\emptyset$)** → no contiene ningún elemento.
- **Contrario ($\bar{A}$)** → se cumple cuando no se cumple A.
- **Compatibles / Incompatibles** → según si comparten elementos.
- **Independientes / Dependientes** → según si uno afecta al otro.

---
# Axiomas de Kolmogorov

Todo lo demás se deduce de aquí:

**1.** $0 \leq P(A) \leq 1$

**2.** $P(E) = 1$

**3.** Si $A \cap B = \emptyset$ → $P(A \cup B) = P(A) + P(B)$

**Regla de Laplace** (casos equiprobables):

$$P(A) = \frac{\text{casos favorables}}{\text{casos posibles}}$$

---
<!-- _class: lead -->
# 02
# Operaciones con Probabilidades
## Unión, intersección y condicionamiento.

---
# Probabilidad de la Unión

**Incompatibles** ($A \cap B = \emptyset$):
$$P(A \cup B) = P(A) + P(B)$$

**Compatibles** ($A \cap B \neq \emptyset$):
$$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

**Complemento como atajo:**

$$P(\text{al menos una vez}) = 1 - P(\text{ninguna vez})$$

* Calcular que algo *no* ocurra suele ser mucho más fácil.

---
# Probabilidad Condicionada

La probabilidad de A **dado que ya ocurrió** B:

$$P(A/B) = \frac{P(A \cap B)}{P(B)}$$

**Sucesos independientes:** $P(A/B) = P(A)$ → conocer B no aporta nada sobre A.

$$P(A \cap B) = P(A) \cdot P(B)$$

**Sucesos dependientes:** $P(A/B) \neq P(A)$

$$P(A \cap B) = P(A) \cdot P(B/A)$$

* Nota: la regla del producto siempre funciona. En independientes se simplifica porque $P(B/A) = P(B)$.

---
## Ejemplo: baraja de 40 cartas

¿Probabilidad de extraer dos ases?

**Con reposición** (independientes):

$$P = \frac{4}{40} \cdot \frac{4}{40} = \frac{1}{100}$$

**Sin reposición** (dependientes):

$$P = \frac{4}{40} \cdot \frac{3}{39} = \frac{1}{130}$$

* La diferencia parece pequeña, pero en problemas reales es crucial.

---
<!-- _class: lead -->
# 03
# Herramientas Prácticas
## Tablas y árboles.

---
# Tablas de Contingencia

Permiten clasificar datos y calcular probabilidades cruzadas de forma visual.

**Ejemplo:** 120 personas, 80 con diabetes.

| | Bajo peso | Normal | Sobrepeso | Total |
|:---:|:---:|:---:|:---:|:---:|
| Con diabetes | 8 | 25 | 45 | **80** |
| Sin diabetes | 2 | 20 | 20 | **40** |
| **Total** | **12** | **43** | **65** | **120** |

- $P(S) = \frac{65}{120} = 0.54$ | $P(S/D) = \frac{45}{80} = 0.56$ | $P(D/S) = \frac{45}{65} = 0.69$

---
# Diagramas de Árbol

Para experimentos **compuestos** (más de un paso).

* Cada nudo representa un paso; cada rama lleva su probabilidad.
* **La suma de las ramas de cada nudo siempre debe dar 1.**
* La probabilidad de un camino completo = producto de sus ramas.

**Ejemplo:** Tres monedas al aire, ¿probabilidad de tres caras?

$$P(3c) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{8}$$

---
<!-- _class: lead -->
# 04
# Teoremas de Probabilidad
## Cuando el azar tiene estructura.

---
# Teorema de la Probabilidad Total

Si $A_1, \ldots, A_n$ son **incompatibles** y su unión es el espacio muestral:

$$P(B) = \sum_{i=1}^{n} P(A_i) \cdot P(B/A_i)$$

**Ejemplo:** Tres cajas con bombillas. Caja 1: 4/10 fundidas; Caja 2: 1/6; Caja 3: 3/8.

$$P(\text{fundida}) = \frac{1}{3} \cdot \frac{4}{10} + \frac{1}{3} \cdot \frac{1}{6} + \frac{1}{3} \cdot \frac{3}{8} \approx 0.314$$

---
# Teorema de Bayes

Dado que ya observamos el resultado, ¿cuál fue la causa?

$$P(A_i/B) = \frac{P(A_i) \cdot P(B/A_i)}{\sum_{j} P(A_j) \cdot P(B/A_j)}$$

- $P(A_i)$ → probabilidades **a priori**
- $P(A_i/B)$ → probabilidades **a posteriori**
- $P(B/A_i)$ → **verosimilitudes**

---
## Ejemplo: alarma de fábrica

$P(\text{incidente}) = 0.1$ | Alarma dado incidente: $0.97$ | Alarma sin incidente: $0.02$

¿Probabilidad de que **no haya incidente** si sonó la alarma?

$$P(\bar{I}/A) = \frac{0.9 \cdot 0.02}{0.1 \cdot 0.97 + 0.9 \cdot 0.02} = \boxed{0.157}$$

* Esto es exactamente lo que está detrás de los filtros de spam, los sistemas de detección de intrusiones y el diagnóstico médico asistido.

---
<!-- _class: lead -->
# Cierre

---
# Lo que aprendimos

**Combinatoria:**
Contar posibilidades de forma sistemática y rigurosa.

**Probabilidad objetiva:**
Cuantificar el azar con matemática.

**Espacio muestral y sucesos:**
El lenguaje formal para operar.

**Tablas y árboles:**
Herramientas para problemas reales.

**Teoremas de Bayes y Probabilidad Total:**
Razonar hacia atrás: encontrar causas a partir de efectos.

---
# La probabilidad como lenguaje

**No es solo tirar dados.**

Es el fundamento detrás de la inteligencia artificial, los sistemas de diagnóstico, las redes de comunicación y la seguridad informática.

* Cada vez que un modelo predice, está usando probabilidad.
* En probabilidad no eliminamos el azar: **aprendemos a convivir con él de forma inteligente**.

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"La probabilidad no trata sobre el azar de los dados; trata sobre la ignorancia humana."*
— Henri Poincaré
