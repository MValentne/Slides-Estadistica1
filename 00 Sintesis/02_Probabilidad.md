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
# Combinatoria y Probabilidad
## Del azar a los números

---
# 00 — ¿Por qué combinatoria primero?

Para calcular probabilidades necesitamos saber **cuántos resultados posibles existen** y cuántos nos **favorecen**. Ahí entra la combinatoria.

La probabilidad de un suceso es un número entre **0** (imposible) y **1** (certeza) que cuantifica el azar de forma rigurosa.

* **A priori:** calculada antes de los ensayos. Al tirar un dado: $P = \frac{1}{6}$.
* **A posteriori:** basada en datos registrados.

---
# 01 — Técnicas de Conteo

| Técnica | Orden | Repetición | Fórmula |
|:---:|:---:|:---:|:---:|
| Variaciones | ✓ | ✗ | $\frac{m!}{(m-n)!}$ |
| Var. con Rep. | ✓ | ✓ | $m^n$ |
| Permutaciones | ✓ | ✗ | $n!$ |
| Perm. Circular | ✓ | ✗ | $(n-1)!$ |
| Combinaciones | ✗ | ✗ | $\frac{m!}{n!(m-n)!}$ |
| Comb. con Rep. | ✗ | ✓ | $\frac{(m+n-1)!}{n!(m-1)!}$ |

**Ejemplo:** Patentes ABC 123 → $27^3 \times 10^3 = 19.683.000$ combinaciones posibles.

---
# 02 — Espacio Muestral, Sucesos y Axiomas

El **espacio muestral** $E$ es el conjunto de todos los resultados posibles. Un **suceso** es cualquier subconjunto de $E$.

**Axiomas de Kolmogorov** — todo lo demás se deduce de aquí:

**1.** $0 \leq P(A) \leq 1$ &emsp; **2.** $P(E) = 1$ &emsp; **3.** Si $A \cap B = \emptyset$ → $P(A \cup B) = P(A) + P(B)$

**Regla de Laplace** (casos equiprobables):

$$P(A) = \frac{\text{casos favorables}}{\text{casos posibles}}$$

---
# 03 — Operaciones con Probabilidades

**Unión compatible:** $P(A \cup B) = P(A) + P(B) - P(A \cap B)$

**Complemento como atajo:**
$$P(\text{al menos una vez}) = 1 - P(\text{ninguna vez})$$

**Probabilidad condicionada** — A dado que ya ocurrió B:
$$P(A/B) = \frac{P(A \cap B)}{P(B)}$$

* **Independientes:** $P(A \cap B) = P(A) \cdot P(B)$
* **Dependientes:** $P(A \cap B) = P(A) \cdot P(B/A)$

---
# 04 — Tablas de Contingencia

Clasifican datos cruzados y permiten leer probabilidades directamente.

| | Bajo peso | Normal | Sobrepeso | Total |
|:---:|:---:|:---:|:---:|:---:|
| Con diabetes | 8 | 25 | 45 | **80** |
| Sin diabetes | 2 | 20 | 20 | **40** |
| **Total** | **12** | **43** | **65** | **120** |

$P(S) = \frac{65}{120} = 0.54$ &emsp; $P(S/D) = \frac{45}{80} = 0.56$ &emsp; $P(D/S) = \frac{45}{65} = 0.69$

* Herramienta especialmente poderosa en medicina y ciencias sociales.

---
# 05 — Diagramas de Árbol

Para experimentos **compuestos**: cada rama lleva su probabilidad, y la suma de las ramas de cada nudo **debe dar 1**.

La probabilidad de un camino completo = **producto** de sus ramas.

**Ejemplo:** Tres monedas al aire, ¿probabilidad de tres caras?

$$P(3c) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \frac{1}{8}$$

---
# 06 — Probabilidad Total y Bayes

**Probabilidad Total** — descomponemos B en todas las rutas posibles:

$$P(B) = \sum_{i=1}^{n} P(A_i) \cdot P(B/A_i)$$

**Bayes** — observado el resultado, ¿cuál fue la causa?

$$P(A_i/B) = \frac{P(A_i) \cdot P(B/A_i)}{\sum_{j} P(A_j) \cdot P(B/A_j)}$$

**Ejemplo:** Alarma de fábrica con $P(I) = 0.1$, $P(A/I) = 0.97$, $P(A/\bar{I}) = 0.02$:

$$P(\bar{I}/A) = \frac{0.9 \cdot 0.02}{0.1 \cdot 0.97 + 0.9 \cdot 0.02} = \boxed{0.157}$$

---
# Lo que aprendimos

**Combinatoria:** contar posibilidades de forma rigurosa antes de calcular.

**Probabilidad objetiva:** cuantificar el azar con matemática.

**Espacio muestral y axiomas:** el lenguaje formal que nos permite operar.

**Condicionada, tablas y árboles:** herramientas para problemas reales.

**Bayes:** razonar hacia atrás — encontrar causas a partir de efectos observados.

* Detrás de los filtros de spam, el diagnóstico médico y la detección de intrusiones hay exactamente esto.

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"La probabilidad no trata sobre el azar de los dados; trata sobre la ignorancia humana."*
— Henri Poincaré
