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

La estadística descriptiva nos enseñó a *mirar* los datos.

La probabilidad nos permite **predecir**: cuantificar el azar con matemática rigurosa.

> Dos enfoques de probabilidad **objetiva**:
> - **A priori:** a partir de casos posibles y favorables *(antes de experimentar)*
> - **A posteriori:** a partir de datos registrados *(frecuencias observadas)*

---

<!-- _class: lead -->
# Técnicas de Conteo

---

# ¿Por qué contar primero?

Para calcular probabilidades necesitamos saber:
- **¿Cuántos resultados posibles existen?**
- **¿Cuántos nos favorecen?**

Aquí entra la **combinatoria**.

---

# Resumen de técnicas de conteo

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

Principio de multiplicación: si un paso tiene $m$ formas y el siguiente $n$, el total es $m \times n$.

---

<!-- _class: lead -->
# Teoría de Probabilidades

---

# Conceptos fundamentales

- **Espacio muestral ($E$ o $\Omega$):** conjunto de todos los resultados posibles
  - Moneda: $E = \{C, X\}$ · Dado: $E = \{1,2,3,4,5,6\}$
- **Suceso:** subconjunto del espacio muestral
- **Suceso seguro ($E$):** todos los resultados posibles → $P(E) = 1$
- **Suceso imposible ($\emptyset$):** sin elementos posibles → $P(\emptyset) = 0$

Si $E$ tiene $n$ elementos, hay $2^n$ sucesos posibles.

---

# Tipos de sucesos

| Tipo | Descripción |
|:---|:---|
| **Compatibles** | Tienen algún elemento en común |
| **Incompatibles** | No comparten ningún elemento |
| **Independientes** | $P(A)$ no se ve afectada por $B$ |
| **Dependientes** | $P(A)$ sí se ve afectada por $B$ |
| **Contrario ($\bar{A}$)** | Se realiza cuando no ocurre $A$ |

---

# Axiomas y propiedades clave

**Axiomas:**

$$0 \leq P(A) \leq 1 \qquad P(E) = 1 \qquad P(A \cup B) = P(A)+P(B) \text{ si incompatibles}$$

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

# Independencia y dependencia

| Caso | Condición | Intersección |
|:---|:---|:---|
| **Independientes** | $P(A/B) = P(A)$ | $P(A \cap B) = P(A) \cdot P(B)$ |
| **Dependientes** | $P(A/B) \neq P(A)$ | $P(A \cap B) = P(A) \cdot P(B/A)$ |

**Ejemplo — baraja de 40 cartas, dos ases:**

$$\text{Con reposición: } \frac{4}{40} \cdot \frac{4}{40} = \frac{1}{100} \qquad \text{Sin reposición: } \frac{4}{40} \cdot \frac{3}{39} = \frac{1}{130}$$

---

# Complemento como atajo

Cuando calcular $P(\text{al menos una vez})$ es difícil:

$$P(\text{al menos una vez}) = 1 - P(\text{ninguna vez})$$

**Ejemplo:** al menos 1 as en 2 extracciones sin reposición (baraja de 40):

$$P(\text{ningún as}) = \frac{\binom{36}{2}}{\binom{40}{2}} = \frac{630}{780} = \frac{21}{26}$$

$$P(\text{al menos 1 as}) = 1 - \frac{21}{26} = \frac{5}{26}$$

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

- Cada nudo origina ramas con sus probabilidades.
- **La suma de probabilidades en cada nudo debe ser 1.**
- La probabilidad de un camino completo es el **producto** de las ramas recorridas.

**Ejemplo — 3 monedas, P(3 caras):**

$$P(3c) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{8}$$

---

<!-- _class: lead -->
# Teoremas de Probabilidad

---

# Teorema de la Probabilidad Total

Si $A_1, \ldots, A_n$ son sucesos **incompatibles** que cubren todo el espacio muestral:

$$P(B) = \sum_{i=1}^{n} P(A_i) \cdot P(B/A_i)$$

**Ejemplo — tres cajas de bombillas:**

$$P(\text{fundida}) = \frac{1}{3} \cdot \frac{4}{10} + \frac{1}{3} \cdot \frac{1}{6} + \frac{1}{3} \cdot \frac{3}{8} \approx 0{,}314$$

---

# Teorema de Bayes

Permite razonar **hacia atrás**: conocida la consecuencia, estimar la causa.

$$P(A_i/B) = \frac{P(A_i) \cdot P(B/A_i)}{\displaystyle\sum_{j} P(A_j) \cdot P(B/A_j)}$$

- $P(A_i)$ → probabilidad **a priori**
- $P(A_i/B)$ → probabilidad **a posteriori**
- $P(B/A_i)$ → **verosimilitud**

---

# Bayes en la práctica

**Ejemplo — alarma de fábrica:**

$P(I) = 0{,}1$ · $P(A/I) = 0{,}97$ · $P(A/\bar{I}) = 0{,}02$

$$P(\bar{I}/A) = \frac{0{,}9 \cdot 0{,}02}{0{,}1 \cdot 0{,}97 + 0{,}9 \cdot 0{,}02} \approx \boxed{0{,}157}$$

> Cuando suena la alarma, hay solo un 15,7 % de probabilidad de que **no** haya habido incidente.

Aplicaciones directas: filtros de spam, diagnóstico médico, detección de intrusiones.

---

<!-- _class: lead -->
# Cierre

---

# Lo que aprendimos

| Concepto | Para qué sirve |
|:---|:---|
| **Combinatoria** | Contar posibilidades de forma sistemática |
| **Probabilidad objetiva** | Cuantificar el azar con matemática |
| **Sucesos y operaciones** | El lenguaje formal para operar |
| **Tablas y árboles** | Resolver problemas reales con orden |
| **Prob. Total y Bayes** | Razonar desde efectos hacia causas |

---

# Reflexión final

**La probabilidad no nos dice qué va a pasar.**

**Nos dice cuán sorprendidos deberíamos estar si algo pasa.**

> *"La probabilidad no trata sobre el azar de los dados; trata sobre la ignorancia humana."*
> — Henri Poincaré

---
<!-- _class: lead -->

# Gracias

**Estadística I — Síntesis**
UNM · FCEQyN · 2025
*Valentino Mende*
