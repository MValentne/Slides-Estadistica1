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
# Probabilidad y Combinatoria
## Del azar a los números

---

# ¿Por qué la probabilidad?

Los datos observados describen lo que *ya ocurrió*.

La probabilidad nos permite ir más lejos: **cuantificar el azar** y razonar sobre lo que *puede ocurrir* con matemática rigurosa.

> Dos enfoques de probabilidad **objetiva**:
> - **A priori:** a partir de casos posibles y favorables *(antes de experimentar)*
> - **A posteriori:** a partir de datos registrados *(frecuencias observadas)*

---

<!-- _class: lead -->
# Técnicas de Conteo
## La combinatoria como base

---

# Resumen de técnicas de conteo

Para calcular probabilidades necesitamos saber cuántos resultados posibles existen y cuántos nos favorecen. Ahí entra la **combinatoria**.

| Técnica | Orden | Repetición | Fórmula |
|:---|:---:|:---:|:---:|
| **Variaciones** | ✓ | ✗ | $\dfrac{m!}{(m-n)!}$ |
| **Var. con repetición** | ✓ | ✓ | $m^n$ |
| **Permutaciones** | ✓ | ✗ | $n!$ |
| **Perm. circular** | ✓ | ✗ | $(n-1)!$ |
| **Combinaciones** | ✗ | ✗ | $\dfrac{m!}{n!(m-n)!}$ |
| **Comb. con repetición** | ✗ | ✓ | $\dfrac{(m+n-1)!}{n!(m-1)!}$ |

---

# Ejemplo: patentes argentinas

Formato **ABC 123** — letras y dígitos pueden repetirse.

$$VR_{27}^3 \times VR_{10}^3 = 27^3 \times 10^3 = 19.683 \times 1.000 = \mathbf{19.683.000}$$

**Principio de multiplicación:** si un paso tiene $m$ formas y el siguiente $n$, el total es $m \times n$.

---

<!-- _class: lead -->
# Teoría de Probabilidades
## Espacio muestral, sucesos y axiomas

---

# Conceptos fundamentales

- **Espacio muestral ($\Omega$):** conjunto de todos los resultados posibles
  - Moneda: $\Omega = \{C, X\}$ · Dado: $\Omega = \{1,2,3,4,5,6\}$
- **Suceso:** subconjunto del espacio muestral
- **Suceso seguro:** $P(\Omega) = 1$ · **Suceso imposible:** $P(\emptyset) = 0$

Si $\Omega$ tiene $n$ elementos, hay $2^n$ sucesos posibles.

| Tipo de suceso | Descripción |
|:---|:---|
| **Compatibles / Incompatibles** | Comparten / no comparten elementos |
| **Independientes / Dependientes** | $P(A)$ no es / sí es afectada por $B$ |
| **Contrario ($\bar{A}$)** | Ocurre cuando no ocurre $A$ |

---

# Axiomas y propiedades clave

**Axiomas de Kolmogorov:**

$$0 \leq P(A) \leq 1 \qquad P(\Omega) = 1 \qquad P(A \cup B) = P(A)+P(B) \text{ si incompatibles}$$

**Propiedades:**

$$P(\bar{A}) = 1 - P(A)$$

$$P(A \cup B) = P(A) + P(B) - P(A \cap B) \quad \text{(compatibles)}$$

**Regla de Laplace** *(sucesos equiprobables):*

$$P(A) = \frac{\text{casos favorables}}{\text{casos posibles}}$$

---

<!-- _class: lead -->
# Probabilidad Condicionada e Independencia

---

# Probabilidad condicionada

Probabilidad de $A$ sabiendo que ya ocurrió $B$:

$$P(A/B) = \frac{P(A \cap B)}{P(B)}$$

**Ejemplo:** ¿Probabilidad de obtener un 6 dado que salió par?

$$P(6/\text{par}) = \frac{P(\{6\})}{P(\text{par})} = \frac{1/6}{3/6} = \frac{1}{3}$$

---

# Independencia, dependencia y complemento

| Caso | Condición | Intersección |
|:---|:---|:---|
| **Independientes** | $P(A/B) = P(A)$ | $P(A \cap B) = P(A) \cdot P(B)$ |
| **Dependientes** | $P(A/B) \neq P(A)$ | $P(A \cap B) = P(A) \cdot P(B/A)$ |

**Ejemplo — baraja de 40 cartas, dos ases:**
$$\text{Con reposición: } \frac{4}{40} \cdot \frac{4}{40} = \frac{1}{100} \qquad \text{Sin reposición: } \frac{4}{40} \cdot \frac{3}{39} = \frac{1}{130}$$

**Complemento** — cuando $P(\text{al menos una vez})$ es difícil de calcular directo:
$$P(\text{al menos 1 as}) = 1 - P(\text{ningún as}) = 1 - \frac{630}{780} = \frac{5}{26}$$

---

<!-- _class: lead -->
# Herramientas para Resolver Problemas

---

# Tablas de contingencia

Clasifican datos cruzando dos variables. Permiten leer probabilidades simples, conjuntas y condicionadas de un vistazo.

| | Bajo peso | Normal | Sobrepeso | **Total** |
|:---|:---:|:---:|:---:|:---:|
| **Con diabetes** | 8 | 25 | 45 | **80** |
| **Sin diabetes** | 2 | 20 | 20 | **40** |
| **Total** | **12** | **43** | **65** | **120** |

$$P(S) = \frac{65}{120} = 0{,}54 \qquad P(S/D) = \frac{45}{80} = 0{,}56 \qquad P(D/S) = \frac{45}{65} = 0{,}69$$

---

# Diagramas de árbol

Útiles para experimentos con **múltiples etapas secuenciales**.

- Cada nudo origina ramas con sus probabilidades
- **La suma de probabilidades en cada nudo debe ser 1**
- La probabilidad de un camino completo es el **producto** de las ramas recorridas

**Ejemplo — 3 monedas lanzadas en secuencia:**

$$P(\text{3 caras}) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{8} \qquad P(\text{al menos 2 caras}) = \frac{4}{8} = \frac{1}{2}$$

---

<!-- _class: lead -->
# Teoremas de Probabilidad

---

# Probabilidad Total

Si $A_1, \ldots, A_n$ son sucesos **incompatibles** que cubren todo el espacio muestral:

$$P(B) = \sum_{i=1}^{n} P(A_i) \cdot P(B/A_i)$$

**Ejemplo — tres cajas de bombillas:**

$$P(\text{fundida}) = \frac{1}{3} \cdot \frac{4}{10} + \frac{1}{3} \cdot \frac{1}{6} + \frac{1}{3} \cdot \frac{3}{8} \approx 0{,}314$$

---

# Teorema de Bayes

Permite razonar **hacia atrás**: conocida la consecuencia, estimar la causa.

$$P(A_i/B) = \frac{P(A_i) \cdot P(B/A_i)}{\displaystyle\sum_{j} P(A_j) \cdot P(B/A_j)}$$

**Ejemplo — alarma de fábrica:** $P(I) = 0{,}1$ · $P(A/I) = 0{,}97$ · $P(A/\bar{I}) = 0{,}02$

$$P(\bar{I}/A) = \frac{0{,}9 \cdot 0{,}02}{0{,}1 \cdot 0{,}97 + 0{,}9 \cdot 0{,}02} \approx \boxed{0{,}157}$$

> Cuando suena la alarma, hay solo un 15,7 % de probabilidad de que **no** haya habido incidente.

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **Combinatoria** | Contar posibilidades de forma sistemática |
| **Probabilidad objetiva** | Cuantificar el azar con matemática |
| **Sucesos y axiomas** | El lenguaje formal para operar |
| **Tablas y árboles** | Resolver problemas reales con orden |
| **Prob. Total y Bayes** | Razonar desde efectos hacia causas |

**La probabilidad no nos dice qué va a pasar — nos dice cuán sorprendidos deberíamos estar si algo pasa.**

> *"La probabilidad no trata sobre el azar de los dados; trata sobre la ignorancia humana."*
> — Henri Poincaré

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
