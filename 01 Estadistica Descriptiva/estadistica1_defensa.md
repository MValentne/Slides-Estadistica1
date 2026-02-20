---
marp: true
theme: academic
math: katex
paginate: true

---
# Estadística I
# UNM - FCEQyN - 2025
## Valentino Mende
### Unidad I

---
<!-- _class: lead -->
# 00
# Introducción a la Estadística
## De datos a predicción

---
# ¿Qué es la estadística?
La estadística es un conjunto de técnicas que, partiendo de la observación de un fenómeno, nos permite conseguir **conclusiones útiles**.
- Nació como herramienta de gobierno para conocer la situación del estado.
* Hoy es una **metaciencia**: aporta herramientas a todas las ciencias.
* Se desarrolló junto a la matemática, aprovechando los avances en **probabilidad**.

---
# Dos grandes ramas
**Estadística Descriptiva:**
Recolectar, clasificar, resumir, hallar regularidades y analizar datos.

**Estadística Inferencial:**
Obtener conclusiones a partir de los datos analizados, generando predicciones con cierto **grado de confianza**.

* Cabe aclarar que estas ramas no son opuestas...
* Se complementan.

---
# Probabilidad y estadística
La probabilidad propone modelos matemáticos para modelar la aleatoriedad. Sin ella, la intuición sería errónea.

### Paradoja del cumpleaños
¿Cuál es la probabilidad de que dos personas compartan cumpleaños en un grupo de 23?

$$P(\text{todos distintos}) = \prod_{k=0}^{22} \frac{365-k}{365} \approx 0.493$$

$$\therefore P(\text{al menos 2 iguales}) = 1 - 0.493 = \boxed{0.507}$$

* ¡Con solo 23 personas, es más probable que sí haya coincidencia!

---
<!-- _class: lead -->
# 01
# Conceptos Fundamentales

---
# Conceptos clave
- **Población (N)**: Conjunto de todas las unidades de análisis del objeto de estudio.
- **Muestra (n)**: Subconjunto significativo y representativo de la población.
- **Parámetro**: Característica numérica de la *población*.
- **Estadístico / Estimador**: Característica numérica de una *muestra*.

---
# Variables
Las variables son propiedades o características de los elementos de una población. Se dividen en:

* **Cuantitativas**: discretas si se cuentan en valores enteros; continuas si requieren medidas intermedias.
* **Cualitativas**: nominales si no siguen un orden; ordinales si sí lo siguen.

---
# Etapas del método estadístico
1. **Planteamiento del problema**: ¿Qué se estudia y por qué?
2. **Fijación de objetivos**: ¿Hasta dónde queremos llegar?
3. **Formulación de hipótesis**: Explicación provisional, susceptible de verificación.
4. **Definición de unidades**: Unidad de observación y de medida.
5. **Determinación de población y muestra**
6. **Recolección** de datos

---
7. **Crítica, clasificación y ordenación**: Se depuran respuestas falsas o inutilizables.
8. **Tabulación**: Se crea una tabla para simplificar la comprensión.
9. **Presentación**: Sin redundancia; solo lo que aporta.
10. **Análisis**: Aquí se cristaliza la investigación. Se redactan conclusiones definitivas.
11. **Publicación**: *"Toda conclusión es digna de ser comunicada en un auditorio."*

---
<!-- _class: lead -->
# 02
# Distribución de Frecuencias
## Agrupando datos...

---
# Tipos de frecuencia
- **Frecuencia absoluta** $(f_i)$: Cantidad de veces que una modalidad fue observada.
- **Frecuencia relativa** $(h_i = f_i / N)$: Proporción respecto al total. Valor en $[0, 1]$.
- **Frecuencia porcentual**: La relativa multiplicada por 100.
- **Frecuencia acumulada** $(F_i)$: Suma progresiva de las frecuencias absolutas.

---
# Intervalos de clase

Un intervalo se usa cuando la variable es cuantitativa continua o los datos son muy numerosos.

**¿Cuántas clases usar?** → Regla de Sturges:

$$k \approx 1 + 3.322 \cdot \log_{10}(n)$$

**¿Cuál es la amplitud?**

$$\text{amplitud} = \frac{\text{Rango}}{k} = \frac{x_{max} - x_{min}}{k}$$

**Marca de clase**: punto medio de cada intervalo → $\frac{L_{inf} + L_{sup}}{2}$

---
# Representación gráfica
- **Histograma**: Gráfico de barras *pegadas* que representa la distribución. Las barras están unidas porque los datos son continuos.
- **Polígono de frecuencias**: Une los puntos medios de cada barra. Útil para comparar distribuciones.
- **Ojiva**: Representación gráfica de la frecuencia *acumulada*. Permite identificar percentiles visualmente.

---
<!-- _class: lead -->
# 03
# Medidas de Tendencia Central
## Resumir datos con un solo valor

---
# Media aritmética
La medida más conocida. Usa **todos** los datos.

$$\bar{x} = \frac{\sum_{i=1}^n x_i}{n}$$

Para datos agrupados en intervalos:

$$\bar{x} = \frac{\sum f_i \cdot x_i}{n}$$

donde $x_i$ es la marca de clase.

* Ventaja: fundamental en métodos estadísticos avanzados.
* Desventaja: **muy sensible a valores extremos**.

---
# Mediana y Moda

**Mediana**: Valor central cuando los datos están ordenados.
- Si $n$ es impar → valor del medio.
- Si $n$ es par → promedio de los dos valores centrales.
* No es afectada por valores extremos.

**Moda**: Valor que aparece con **mayor frecuencia**.
- Puede no existir, o haber varias (distribución bimodal).
- Puede usarse con variables **cualitativas**.

---
# Relación entre las tres medidas

En una **distribución simétrica**:

$$\text{Media} = \text{Mediana} = \text{Moda}$$

En una **distribución asimétrica positiva** (cola derecha):

$$\text{Moda} < \text{Mediana} < \text{Media}$$

En una **distribución asimétrica negativa** (cola izquierda):

$$\text{Media} < \text{Mediana} < \text{Moda}$$

---
<!-- _class: lead -->
# 04
# Medidas de Posición
## Cuartiles, deciles y percentiles

---
# ¿Qué son las medidas de posición?
Dividen el conjunto de datos ordenados en partes iguales. Permiten **ubicar un dato respecto al resto** de la distribución.

- **Cuartiles** $Q_1, Q_2, Q_3$ → dividen en 4 partes iguales. $Q_2$ = Mediana.
- **Deciles** $D_1 \ldots D_9$ → dividen en 10 partes iguales. $D_5$ = Mediana.
- **Percentiles** $P_1 \ldots P_{99}$ → dividen en 100 partes iguales. $P_{50}$ = Mediana.

*Ej.: estar en el percentil 80 significa superar al 80% de los demás.*

---
# Rango intercuartílico e identificación de outliers

$$IQR = Q_3 - Q_1$$

Mide la dispersión del **50% central** de los datos. Es robusto frente a valores extremos.

Un valor es **atípico (outlier)** si:

$$x < Q_1 - 1.5 \cdot IQR \quad \text{o} \quad x > Q_3 + 1.5 \cdot IQR$$

* Todo esto se visualiza con el **boxplot (diagrama de caja)**: representa $Q_1$, $Q_2$, $Q_3$, mínimo, máximo y outliers.

---
<!-- _class: lead -->
# 05
# Medidas de Dispersión
## ¿Qué tan dispersos están los datos?

---
# ¿Por qué medir la dispersión?
Dos conjuntos de datos pueden tener la **misma media** pero diferir mucho en cómo están distribuidos.

**Conjunto A:** 10, 12, 15, 18, 20 → media = 15

**Conjunto B:** 5, 10, 15, 20, 25 → media = 15

* La dispersión indica la **variabilidad** de los datos.
* La media es más representativa cuando la dispersión es **baja**.

---
# Rango y varianza

**Rango**: medida más simple.

$$\text{Rango} = x_{max} - x_{min}$$

Fácil de calcular, pero muy sensible a extremos.

**Varianza**: mide la dispersión promedio respecto a la media.

$$\sigma^2 = \frac{\sum (x_i - \mu)^2}{N} \quad \text{(poblacional)}$$

$$s^2 = \frac{\sum (x_i - \bar{x})^2}{n - 1} \quad \text{(muestral)}$$

---
# Desviación estándar

Raíz cuadrada de la varianza. Se expresa en las **mismas unidades** que la variable.

$$s = \sqrt{s^2}$$

- $s$ pequeña → datos concentrados alrededor de la media.
- $s$ grande → alta variabilidad.

**Desviación intercuartílica:**

$$DI = \frac{Q_3 - Q_1}{2}$$

No depende de valores extremos.

---
# Distribución Normal (Campana de Gauss)
Modelo teórico de distribución simétrica. Sirve como referencia para comparar.

- Simétrica respecto a la media
- Media = Mediana = Moda
- Área total bajo la curva = 1
- La **media** fija el centro; la **desviación estándar** fija la amplitud.

* Muchos fenómenos naturales y sociales se aproximan a esta distribución.

---
<!-- _class: lead -->
# 06
# Medidas de Forma
## Asimetría y curtosis

---
# Asimetría
Describe hacia dónde se extiende la **cola** de la distribución.

- **Distribución simétrica**: Media = Mediana = Moda.
- **Asimetría positiva**: la cola se extiende hacia la derecha. Moda < Mediana < Media.
- **Asimetría negativa**: la cola se extiende hacia la izquierda. Media < Mediana < Moda.

La asimetría describe hacia dónde se extiende la cola.

---
# Curtosis
Mide el grado de concentración de los datos alrededor de la media. Indica qué tan "picuda" o "achatada" es una distribución.

$$g_2 = \frac{\frac{1}{n} \sum (x_i - \bar{x})^4}{s^4}$$

En la distribución normal, la curtosis es **3**.

Por eso se define: **Exceso de curtosis** $= g_2 - 3$

- Exceso $= 0$ → **Mesocúrtica** (similar a la normal)
- Exceso $> 0$ → **Leptocúrtica** (más picuda, colas pesadas)
- Exceso $< 0$ → **Platicúrtica** (más achatada, colas livianas)

---
# Conexión con la distribución normal

La distribución normal es el **modelo de referencia** para comparar otras distribuciones.

- Asimetría $= 0$
- Curtosis $= 3$

* En estadística descriptiva no buscamos predecir ni validar hipótesis.
* Buscamos **comprender y comunicar claramente** la información contenida en los datos.

---
<!-- _class: lead -->
# Cierre

---
# Lo que aprendimos

**Estadística descriptiva:**
Organizar, resumir y visualizar datos.

**Medidas de tendencia central:**
Encontrar el corazón de nuestros datos.

**Medidas de dispersión:**
Entender su variabilidad.

**Medidas de forma:**
Describir su distribución completa.

---
# Más allá de los números

Los conceptos vistos no son fórmulas aisladas.

Son herramientas para:
- Resumir y organizar información.
- Describir el comportamiento de los datos.
- Comparar distribuciones.
- Extraer conclusiones basadas en evidencia.

**La estadística no elimina la incertidumbre.**
**Nos enseña a cuantificarla, comprenderla y trabajar con ella.**

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"En Dios confiamos, todos los demás deben traer datos."*
— W. Edwards Deming
