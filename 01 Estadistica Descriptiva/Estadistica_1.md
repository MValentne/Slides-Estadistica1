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
# 00
# Introducción a la Estadística
## De datos a predicción
---
# Origen
La palabra estadística surge de la noción del estado; de la recolección, organización, conservación y tratamiento de datos DEL ESTADO.
- Era una herramienta de gobierno para conocer la situación del estado.
* Hoy en día ha evolucionado a ser una **metaciencia**.
* Aporta herramientas fundamentales a todas las otras ciencias.
---
La estadística se desarrolló a la par que la matemática, aprovechando en particular los avances en probabilidad.
- Probabilidad --> Propone modelos matemáticos para modelar la aleatoriedad.
- Es la base para la estadística inferencial. (más de esto después)
- Estadística --> Aprovecha tales modelos para entender datos.
- El uso de modelos y cálculo probabilístico en muchas ocasiones nos ayuda a comprender aquello en lo que la simple intuición sería errónea.
* Paradoja del cumpleaños...
---
# Paradoja del cumpleaños
¿Cuál es la probabilidad de que una persona coincida en cumpleaños con otra en un grupo de 23 personas?
* "Yo creo que es prácticamente imposible..."
* ¡Resulta que es bastante probable!
### Desarrollo:
* Para 2 personas, la probabilidad es de P(c_1 = c_2)
* Para 3 personas, P(c_1 = c_2, c_1 = c_3, c_2 = c_3)
* ¿Un posible problema de conteo? (más de esto adelante)
---
Para ver cuántas posibilidades distintas (cuántos escenarios) existen, podemos verlo como un problema de conteo. 
Visto de esta forma:
* Si tenemos un grupo de 20 personas, queremos ver cuántas concordancias de 2 personas pueden haber, ¡cuántas combinaciones pueden formar!
* 20C2 --> 20 personas en elección por par
* 20C2 = 190 posibilidades!
* Y volviendo al problema del inicio...
* 23C2 = 1770 posibilidades!
* (Todo esto para hacernos una idea de la magnitud del problema que pasa desapercibida!)
---
**P(todos distintos) para 23 personas**

$$P(\text{todos distintos}) = \frac{365}{365} \times \frac{364}{365} \times \frac{363}{365} \times \cdots \times \frac{343}{365}$$

$$= \prod_{k=0}^{22} \frac{365-k}{365} \approx 0.493$$

$$\therefore P(\text{al menos 2 iguales}) = 1 - 0.493 = \boxed{0.507}$$
---
## En R (para los curiosos)
```r
# Cálculo directo
n <- 23
prob_distintos <- prod((365 - 0:(n-1)) / 365)
1 - prob_distintos  # 0.5072972

# Simulación
cumpleanos <- sample(1:365, 23, replace = TRUE)
any(duplicated(cumpleanos))  # TRUE/FALSE

# Función de R nativa
pbirthday(23)  # 0.5072972
```
---
## Retomando...
La probabilidad se utiliza en una amplia cantidad de campos, entre ellos:
- Medicina, 
- Comunicaciones, 
- Economía, 
- Finanzas 
- y en nuestro caso de interés, **Informática**.
* ¡Un ejemplo claro aplicado al campo, la **Teoría de la Información**!
---
# Bits de Información (Entropía de Shannon)

**Fórmula general:** cantidad de información al observar un evento con probabilidad $p$

$$I(p) = -\log_2(p) = \log_2\left(\frac{1}{p}\right) \text{ bits}$$

---

**Moneda justa:** $p = \frac{1}{2}$

$$I = \log_2(2) = 1 \text{ bit}$$

**Dado de 6 caras:** $p = \frac{1}{6}$

$$I = \log_2(6) \approx 2.585 \text{ bits}$$

*Interpretación: el dado nos da ~2.6 veces más información que la moneda*

---
<!-- _class: lead -->
# La Estadística
## Nos adentramos un poco más...
---
Al hablar de estadística nos llega a la mente un conjunto de datos a estudiar, usualmente llamado "dataset"
- Una representación ordenada y sistemática de los datos
* Hoy en día podemos extraer un dataset de prácticamente cualquier tópico.
* véase [Google Dataset Research](https://datasetsearch.research.google.com/)
* véase [TidyTuesday](https://github.com/rfordatascience/tidytuesday?utm_source=chatgpt.com)
---
Para ciertos campos, la estadística resulta ser la herramienta principal para dar luz y obtener resultados.
- Esta es más visible en las ciencias sociales.
- Está fuertemente integrada en la estructura de otros campos, tales como:
* Física
* Biología y Medicina
* Ciencia de datos / Machine learning
* Economía
* Etc.
--- 
La estadística se encarga de los métodos y procedimientos para recoger, clasificar, resumir, hallar regularidades y analizar los datos; siempre y cuando la variabilidad e incertidumbre de tales datos correspondan a la naturaleza propia de estos y no de algún factor externo. 
* **Ejemplifiquemos...**
---
Tiramos 100 veces una moneda...
* Algunas veces sale cara, algunas veces sale cruz.
* Es la naturaleza de la moneda, por lo que podemos emplear estadística.

Nos subimos a una balanza mal calibrada, la medición es incorrecta por 5kg...
* La balanza tiene un problema, por lo que no se aprecia la naturaleza de la balanza.
* No empleamos estadística. 
---
# La Estadística Descriptiva
Se encarga de los métodos y procedimientos para:
- Recoger
- Clasificar
- Resumir
- Hallar regularidades
- Analizar datos
---
# La Estadística Inferencial
Obtiene conclusiones a partir de tales datos analizados previamente, con la finalidad de generar predicciones con cierto grado de confianza.

---
## En vista general...

La estadística entonces dejó de ser una técnica centrada en los estados para convertirse en una herramienta imprescindible de todas las ciencias.

La estadística hace inferencias sobre una población, partiendo de una muestra significativa de esta.

---

## Ya hablamos un poco sobre la estadística, pero cabe concretar conceptos.

---
# Importancia y definición
La estadística es un conjunto de técnicas que, partiendo de la observación de un fenómeno, nos permite conseguir conclusiones útiles. 
* La estadística descriptiva se encarga de la recolección, clasificación y descripción de datos muestrales o poblacionales para su interpretación y análisis
* La estadística inferencial (o matemática) se basa en la predicción. Desarrolla modelos teóricos que se ajustan a una determinada realidad con cierto grado de confianza. 
* Cabe aclarar que estas ramas no son opuestas...
* Se complementan.
---

<!-- _class: lead -->
# 01
# Conceptos Fundamentales
## Entramos en contexto, ahora vamos a los detalles.
--- 
# Etapas del método estadístico
1. **Planteamiento del problema**: ¿Qué se estudiará y por qué se tiene que estudiar? Recurrimos a la revisión bibliográfica del tema (ver investigaciones previamente realizadas).
2. **Fijación de objetivos**: Fijamos metas y objetivos; hasta dónde se desea presupuestar, hasta dónde queremos llegar. 
3. **Formulación de hipótesis**: Una explicación provisional de los hechos y el objeto de estudio. Una hipótesis estadística debe ser susceptible a probar su veracidad. (Hipótesis nula y alternativa son temas de los que se hablará a futuro.)
---
4. **Definición de la unidad de observación y de la unidad de medida**: La unidad de observación corresponde a cada uno de los elementos de la población observada, mientras que la unidad de medida habla de la medida en la que se analizan las variables estudiadas. (metros, kilos, litros...)
5. **Determinación de la población y de la muestra**: En notación conjuntista diríamos que la población es el universo (nuestro dataset entero), mientras que la muestra es un subconjunto de tal universo; un subconjunto significativo, representativo de toda la población (usualmente optamos por esta última, estudiamos un pedazo para entender el todo).
6. **La recolección**: En pocas palabras, la encuesta. Descubrir dónde está la información, cómo y a qué costo conseguirla. Se obtiene una aproximación de la variabilidad de población. 
---
7. **Crítica, clasificación y ordenación**: Se depuran las respuestas falsas o inutilizables, aquellas que están fuera de lugar para lo que queremos estudiar. Dejado de lado el material desechado, se clasifica y ordena la información (usualmente se emplea cómputo en esta etapa).
8. **La Tabulación**: Se crea una tabla para simplificar la comprensión de la información a quien la esté analizando. Es de suma importancia la inclusión de elementos como un título adecuado, subtítulos internos y cuantificación de las variables, y notas de pie de cuadro que otorguen claridad o créditos a quien corresponda.
9. **La presentación**: Se trabaja en el informe, se presenta de la forma adecuada. No deseamos redundancia; gráficos y tablas que no proporcionen información relevante, esto solo es confuso. 
--- 
10. **El análisis**: Es donde se cristaliza la investigación. Buscamos establecer y redactar las conclusiones definitivas. Se determinan los parámetros y estadísticos muestrales para las estimaciones e inferencias sobre la población.	
11. **Publicación**: "Toda conclusión es digna de ser comunicada en un auditorio". Buscamos dar a luz nuestra investigación. Es posible que otros investigadores o estudiosos estén interesados en nuestro trabajo.
---
# Conceptos clave
- **Unidad de análisis**: Un elemento de la población/universo que se está estudiando
- **Población o universo**: Representa un conjunto de todas las unidades de análisis que conforman el objeto de estudio. Se representa con (N).
- **Muestra**: Subconjunto significativo de la población. Se representa con (n).
- **Parámetro**: Cualquier función (dígase, función estadística como media aritmética) que determine una característica numérica de la población.
---
- **Estadístico/Estimador**: Característica numérica de una muestra (Nuevamente una función, esta vez aplicada a un subconjunto).
- **Variables**: Propiedades, características, cualidades... de los elementos de una población. Se dividen en:
* Cuantitativas: discretas en caso de que sea contado en valores enteros, continuas en caso de requerir medidas intermedias entre valores (fraccionarias).
* Cualitativas: nominales si no siguen un criterio u orden, y ordinales si es que sí lo siguen.
---

<!-- _class: lead -->
# 02 
# Distribución de frecuencia
## Agrupando datos...

---
# Sobre la distribución de frecuencias
Habla de agrupaciones de datos según su clase, a esta clase se le denomina modalidad del carácter estadístico.
Ejemplo:
| Tamaño (KB) | Frecuencia Absoluta (fᵢ) | Frecuencia Acumulada (Fᵢ) |
|:---:|:---:|:---:|
| 0 – 100 | 22 | 22 |
| 100 – 200 | 35 | 57 |
| 200 – 300 | 24 | 81 |
| 300 – 400 | 13 | 94 |
| 400 – 500 | 6 | 100 |
| **Total** | **100** | — |

---
En el esquema anterior se muestra una organización de datos mediante una tabla.
El objetivo es acomodar el dataset de forma útil para simplificar el análisis de la información contenida. 
* **Frecuencia absoluta**: Cantidad de veces que una modalidad ha sido observada (dígase el número de veces que aparece dicho valor de la variable)
* se representa con f[i].
* **Frecuencia relativa**: Tiene relación con la cantidad total del tamaño de muestra.
* dígase: _h[i] = Fr = fi/N_, que da de resultado un valor entre [0,1].
* Al multiplicar por 100, pasa a ser una frecuencia porcentual.
---
- **Frecuencia absoluta acumulada**: Es la suma progresiva de las frecuencias absolutas de cada clase o intervalo. 
* En pocas palabras, dice cuántos datos hay hasta tal modalidad.
* Cabe especificar que la variable debe ser cuantitativa o cualitativa ordenable para que esta tenga sentido.
---
# Intervalos de clase
Un intervalo se usa cuando una variable es cuantitativa continua o los datos son discretos, pero muy numerosos. 
Llamaremos amplitud, longitud o ancho del intervalo a la diferencia entre el extremo inferior del intervalo y el inferior del siguiente intervalo.

---
**Ejemplo:**

|   |   límite inferior |   límite superior |
|:---:|:---:|:---:|
| [10,15)  |   10   |               15
| [15,20)  |   15   |               20
|[20,25)   |  20    |              25
| [25,30)  |   25   |               30
---

## Algunas ideas clave
**Marca de clase**: Punto medio de cada intervalo, dígase: [15,20], Marca de clase = (15+20)/2 = 17.5
- Surgen 3 preguntas de interés:
1. ¿Cuántas clases deben usarse?
2. ¿Cuál debe ser la amplitud de clase?
3. ¿En qué valor debe empezar la primera clase?
---
# 1. ¿Cuántas clases deben usarse?

- Evitar demasiadas clases.
- Evitar muy pocas clases.

Una guía: la **regla de Sturges**

$$k \approx 1 + 3.322 \cdot \log_{10}(n)$$

Donde $n$ es el número total de datos.

No es absoluta, pero es un buen punto de partida.

---

## Ejemplo de aplicación

Para $n = 100$:

$$k \approx 1 + 3.322 \cdot \log_{10}(100)$$
$$k \approx 1 + 3.322 \cdot 2 = 7.64 \approx 8$$

Para $n = 500$:

$$k \approx 1 + 3.322 \cdot \log_{10}(500)$$
$$k \approx 1 + 3.322 \cdot 2.699 = 9.97 \approx 10$$

---

# 2. ¿Cuál debe ser la amplitud de clase?

$$\text{Amplitud} = \frac{\text{Rango}}{k}$$

Donde:

$$\text{Rango} = \text{Máximo} - \text{Mínimo}$$

y $k$ es el número de clases.

---

## Ejemplo

Datos: entre 10 y 110

$$\text{Rango} = 110 - 10 = 100$$

Si se decide usar $k = 10$:

$$\text{Amplitud} = \frac{100}{10} = 10$$

Clases:
$[10, 20), [20, 30), \ldots, [100, 110)$

---

# 3. ¿En qué valor debe empezar la primera clase?

Generalmente se usa el **valor mínimo** de los datos.

Esto simplifica la lectura de la tabla.

A veces se redondea hacia abajo para que sea un valor "limpio".

---

# Distribución de frecuencias en R
```r
# Crear intervalos
datos <- c(12, 15, 18, 22, 25, 28, 30, 33, 35, 40)
intervalos <- cut(datos,
                  breaks = c(10, 20, 30, 40),
                  right = FALSE)

# Tabla de frecuencias
table(intervalos)
```

---

# Representación gráfica: el histograma

Un histograma es un gráfico de barras que representa una distribución de frecuencias.

Cada barra corresponde a un intervalo, y su altura refleja la frecuencia.

**Diferencia con un gráfico de barras común:**
En el histograma las barras están pegadas, ya que representan datos continuos.

---

# Ejemplo de histograma

![Ejemplo de histograma](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Histogram_of_arrivals_per_minute.svg/600px-Histogram_of_arrivals_per_minute.svg.png)

Representa la distribución de valores agrupados en intervalos.

---

# Polígono de frecuencias

Se construye uniendo con líneas los puntos medios de cada barra del histograma.

- Es útil para comparar distribuciones.

---

# Ejemplo de polígono de frecuencias

![Polígono de frecuencias](data:image/jpeg;base64,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)

- Se construye uniendo los puntos medios de las barras del histograma.

---

# Ojiva

Representación gráfica de la frecuencia acumulada.

Muestra cuántos datos hay hasta cada intervalo.

Puede ser absoluta o relativa.

---

# Ejemplo de ojiva

![Ejemplo de ojiva](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASYAAACrCAMAAAD8Q8FaAAABtlBMVEX///+2tra7u7vx8fHLy8vt7e3Pz8/Dw8PY2Njl5eX4+PgAAABnkMNaiMBPgb24uLhEe7ozcrYsbrTt8vj5+/2+z+Xc5fF9oMw+eLiju9o2dLdYNAAALHJ+pMr/79j///2PrdO7zeTI1unr/f+Xl5dxmMiYs9bn7vb2///wwJAqAACbZyMAAEPa9/////Gtwt7//+i91/jQw6oyAAAfU3/n2c2JWyFigKylcTcAACefekXl8t1oRB0AADXL4PqyimpklrTd1cBOGgDmwJvs7c5dR2vfz6FfmsFUCwAlb6IAJGPe7+324s4/EAAAQXpkj7ZlNwD//s/a3L0eAABqp8XOtaOTobSmeFMAABzR/f/XyI8gX5DOuZV4ssiGhIFKKAAAADrx0Z4NXp//5LVjJQCRwtxjYDgHMFgdSl17dFCPi4aDi5ejkJG2qZ7UuqiBgHq8xqpldJ+kfGt6gJeXgmxKT1zKqHyhoaFMbY2SuLqOdGhxa4XdtZaiscWRZ1p5cWp8anabxtKFg2PBno1DN0K74e1xiauUdGzInGqypbhgX1dzXm+hy89oPD0UOFFxh4SejWFQZYjWE/GoAAAIvUlEQVR4nO2d/V/bxh2AzzY2tvWCXmxJdoYtC1t2tiIBi8vSjbgtlHYJa0bbOF3Wkm0Z2xoIaSGBJUsWGIOs67au//FOst19AKOTbb37nh/kFx3y+fncHbq7750BwGAwGAwGg8FgokR54ccEcU2Az5pvEgSx2LhKyD+5Pg+A9tYbP/0ZfGfpht9ZDAIt4u3kO+9evwGWiWvpzMp7s1eJ6VXifQBKH/y8dOXmrUwm53cWA8DaLz6Ex6vEbe2XNxvmO1BT6coPGuC3hAof/c1dYDALDlj/4a8/+vgTcKdabeegJnCXmC/f/fRXpStL1arudxaDwD3iE2Bq+oz4HNzZuP8bo9LBkvR+6d3fAajp242C31kMAqsEBY8PiMWPPr4N2/MfvWFq0n7/4QKxCXCl61G6f3MGlFuEqr25dPK9pvJb1//wx1ms6f98Rvyp+gWxCBvzDz7denh/ydQE23GCNhwuVTe2BL+zGAjmHla3Zs1nx9Xq1gxYq+bhTdN29QQeH1XhW1gTBoPBYDAYDAYztpR32vC49rjd8DsngWbuy6/gMQ125/3OSbBZNzSB0t6M8ZCaSE1gOiQuaspu180XiWwsm8CYnLGkPXlaWCnsP91SOq9jbpfeaIA12QJrsgXWZAusyRZYky2wJltgTbbAmmyBNdkCa7IF1mQLrMkWWJMtsCYrdnqxH+OqKa/aSLTweLP7bEw1KTRjx9O9TphjMhFLJMePhELT0NPZN7P9NHVKUyp1kBpD0ioDNcln3+yjqfnFn7uN09RwhTbUKCIrMZKMTpjNZrsB/ePXNilkkVF5ZbDg6jHTlMvXWLpQH/jvxktTnmSZAj/EH46TpgrF0fpwq4fGRhOv0yw19KKYMdHEFyiWrAy/Dm0sNPEFukjlR1msNwaaeJXhSGW0a0ReU11m2dqIkiKvSZCZoujASphIaxJESXJCUmQ1KRVDEsvJDq2piqamPMMUSK4oD94ruYRIalKMcRJJHaZX0iOZaQBQzmS6L6OoKScbmkZaX72215oGoPXseXcDiQhq0kmWZmyN4V7O8fzcX2bAi2db3WobtWE5Xpc4qgIqI67Vf2FqunPw0CxN8anqVCwyTMXbiwxXexmLx6YG/lpTZ0J5l093prX6X09a3amVKJWmukpLNcWRfVbKzXhDU0rxycgN8ho33KP3Si4hKpoEkWOdueHuSzQ0KSQrqY7dS/YhAppyClmkXZUUAU25CjnUXMlghFxTTqc5ZshpgEEItSa+YN5LekCINdVVeAeQ9+azwqmpooC6TBcdupe0QSg15WlaLjowwm2fEGqCvVuaZkhP93oKmSZeUEmmyNC05EnL/T0h0sQLhRrFSpRYKdCMx3s/hkWToIsUV2RqumC02qrXWz+GQZNQERmOK0JFnn1k6dXzTXg87O12F3BNOaiIllha9FCRwb5ujF7ePepMGWQyB8lM4EjqCsxVMlnPyyTDSfTtSjrjfjbPhKh2BnnvPts1Ry/T6YN08JhmmJep9iLDsgylKoJHn3pG0768ftoArdnl4A7y6sb0UZFlaVVxu+N/KeXjvZkVtbTR23EngG0TadwWyflRJiMdJ2iackqNgZo86tHaJliaoCRY1+qyt7fYNgiUpjzJSUPFI7tOcDQZA5F0UPefD4omXh8t1NZlgqGJL1DFAEsKhia+QLOjxSO7jv+a6mpx5Hhk1/FbkyBLrBh0SX5rEqYZh0JtXcZPTYJcdCRo2wP80yTUWNa5UFuX8UOTXjdjSBiXwyOcxAdNBYY0Y0gC2Svpoh0fnsCHd/Z8G0gpGOMkjOsxJKOxL69/1QBzf+vsyevDsFyOhkhBb7g7g7zHt7ZNTR5H8k7FD06lIsPQL4MXP3w2kne/sA7r2+7jvx91XntammD/ViIrfAhuJ0uvDk9WVKB93a10HrZN5npbo+sW6N5bfzzTZCwlpYJfjC7BI02CzHIhqGuX4okmQZTC0iu5BA80CXJI+rcWuK5JEEPTv7XAZU1KzcmlpP7hqibYvw1218027mkadqukQOKaJnONRCRKksHAmnLIeSIjgT78VkmBZGBNoiRaJ1AlUmdYb9ZIeMaAmniRoWnSEmM4KeCzboMzgKacUhBpyRguoiwwztOhv086j01NUFGtyHFSTacZxlICDxOEuPPWpbxzMAtA6aDXdNjQVM/LNMexlFwx/rsLqFUQfOCncG2wPL162gA7t153d7WwHpbj6xWRYop0TQ1WjJ/rdAZ5gbZh/kT6xUHe7j4HU/FYrN0WSYmlydN2OxaPB29Y1lnODfLOzxmTKse9Sne+NOU6JwRdpthikfIxmNZX1p6+3lzR/3HtoP8qg1xNUmFrzXIcI+qeLeoLINkEKOey2UTfXS140thIm6XEzgoaTI+zmgTDEiWMV3Nth3OVToGWsKSLnL9vUrClfvgdLRcSsCZbYE22wJpsgTXZAmuyBdZkC6zJFliTLbAmC8qZ3jAS1mTB/tvPTzrPArjAPjCUD8EDc1JycvJgEsEEKoEXIDPhQC4T/TStThtPsrDSZS1BJsim06MmSKESOJHLFCpB+mJxah0ddysdsm1CJkhnXE/gQC4zfSwgE2jx3lxaEnV9ZIJsv19THChBApXAiVxerFPnEiAzgcFgMBjM+NBExAxoE6gQr+YEagorbZ2g3ER9hjaBiA1qTkxYf4/yRKphfQlLFl5tWie4M3l4wzLB3NcLt60vsfbPI8vz2jcphKZtlMdmqmW9M2brX7vz1pew5h7q127Kr601gRePERnY/hKh6d9bJ5YJHvxnA7WBkXY4Y3l++du9kaZt76H2Jz1GbrFUes/y9NXvnuxZfwcw941ljXhQQ1kAy7L1+ePYk1FKU/K/p9aV+sV3k9YJSu1Hp5YJstnVzy0TaJOIK8wdPtqyblm0w1nL82D3qIVoXSxJphHtayadQpTWZhoV85O1voKWQl2hmUIUJg0VvJZNI3OJwWAwGAwGg8GMThxjg/8BcmMo9TuknCEAAAAASUVORK5CYII=)

- Se usa para identificar percentiles y analizar tendencias acumuladas.

---

<!-- _class: lead -->
# 03
# Medidas de Tendencia Central
## Resumir datos con un solo valor

---

# ¿Qué es una medida de tendencia central?

Es un valor que representa el **centro** de un conjunto de datos.
* (Esta idea de "centro" es relativa a la medida empleada)

Permite resumir un dataset con un solo número representativo.

---

# Principales medidas de tendencia central

- **Media aritmética** (promedio)
- **Mediana**
- **Moda**

Cada una tiene ventajas y desventajas según el tipo de datos.

---

# Media aritmética

La más conocida y usada.

$$\bar{x} = \frac{\sum_{i=1}^n x_i}{n}$$

Se suman todos los valores y se divide por la cantidad total.

---

## Ejemplo

Datos: 10, 15, 20, 25, 30

$$\bar{x} = \frac{10 + 15 + 20 + 25 + 30}{5} = \frac{100}{5} = 20$$

La media es **20**.

---

# Ventajas de la media

- Usa **todos** los datos.
- Es fácil de calcular.
- Es fundamental en métodos estadísticos avanzados.

---

# Desventajas de la media

- **Muy sensible a valores extremos.**

Ejemplo:

Datos: 10, 15, 20, 25, **1000**

$$\bar{x} = \frac{10 + 15 + 20 + 25 + 1000}{5} = 214$$

¿Representa bien a los datos?

---

# Media para datos agrupados

Si los datos están en intervalos:

$$\bar{x} = \frac{\sum f_i \cdot x_i}{n}$$

Donde:
- $f_i$ es la frecuencia de cada clase
- $x_i$ es la marca de clase

---

## Ejemplo con datos agrupados

| Intervalo | Marca ($x_i$) | Frecuencia ($f_i$) | $f_i \cdot x_i$ |
|:---:|:---:|:---:|:---:|
| [10, 20) | 15 | 3 | 45 |
| [20, 30) | 25 | 5 | 125 |
| [30, 40) | 35 | 2 | 70 |

$$\bar{x} = \frac{45 + 125 + 70}{3 + 5 + 2} = \frac{240}{10} = 24$$

---

# Mediana

Es el **valor central** cuando los datos están ordenados de menor a mayor.

- Si hay una cantidad **impar** de datos, es el valor del medio.

- Si hay una cantidad **par** de datos, es el promedio de los dos valores centrales.

---

## Ejemplo con cantidad impar

Datos: 10, 15, **20**, 25, 30

La mediana es **20**.

---

## Ejemplo con cantidad par

Datos: 10, 15, **20**, **25**, 30, 35

$$\text{Mediana} = \frac{20 + 25}{2} = 22.5$$

---

# Ventajas de la mediana

- **No es afectada por valores extremos.**

Ejemplo:

Datos: 10, 15, 20, 25, 1000

La mediana sigue siendo **20**.

Útil cuando hay valores atípicos.

---

# Moda

Es el valor que **aparece con mayor frecuencia**.

Puede no existir, o puede haber **varias modas**.

---

## Ejemplos

**Datos 1:** 10, 15, **20**, **20**, 25, 30

La moda es **20**.

**Datos 2:** 10, **15**, **15**, 20, **25**, **25**, 30

Hay dos modas: **15 y 25** (distribución bimodal).

**Datos 3:** 10, 15, 20, 25, 30

No hay moda.

---

# Ventajas de la moda

- Puede usarse con datos **cualitativos**.

Ejemplo:
Colores preferidos en una encuesta.

- Fácil de identificar visualmente en gráficos de frecuencias.
---

# Comparación de las tres medidas

| Medida | Ventaja | Desventaja |
|:---:|:---:|:---:|
| **Media** | Usa todos los datos | Sensible a extremos |
| **Mediana** | Robusta a extremos | No usa todos los datos |
| **Moda** | Funciona con cualitativos | Puede no existir |

---

# Relación entre media, mediana y moda

En una **distribución simétrica:**

$$\text{Media} = \text{Mediana} = \text{Moda}$$

En una **distribución asimétrica:**

Difieren entre sí.

---

# Ejemplo de distribución simétrica

![Distribución simétrica](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Normal_Distribution_PDF.svg/400px-Normal_Distribution_PDF.svg.png)

Media = Mediana = Moda

---

# Ejemplo de distribución sesgada a la derecha

![Sesgo a la derecha](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Negative_and_positive_skew_diagrams_%28English%29.svg/446px-Negative_and_positive_skew_diagrams_%28English%29.svg.png)

$$\text{Moda} < \text{Mediana} < \text{Media}$$

---

# En R

```r
datos <- c(10, 15, 20, 25, 30)

# Media
mean(datos)

# Mediana
median(datos)

# Moda (no hay función nativa)
tabla <- table(datos)
names(tabla)[which.max(tabla)]
```

---

<!-- _class: lead -->
# 04
# Medidas de Posición
## Cuartiles, deciles y percentiles

---

# ¿Qué son las medidas de posición?

- Dividen el conjunto de datos ordenados en partes iguales.

- Permiten ubicar un dato respecto al resto de la distribución.

---

# Cuartiles

Dividen los datos en **4 partes iguales**.

$$Q_1, Q_2, Q_3$$

- **Q₁**: primer cuartil (25%)
- **Q₂**: segundo cuartil (50%) = **Mediana**
- **Q₃**: tercer cuartil (75%)

---

## Interpretación

**Q₁**: el 25% de los datos están por debajo.

**Q₂**: el 50% de los datos están por debajo.

**Q₃**: el 75% de los datos están por debajo.

---

# Deciles

Dividen los datos en **10 partes iguales**.

$$D_1, D_2, \ldots, D_9$$

**D₅** = mediana

---

# Percentiles

Dividen los datos en **100 partes iguales**.

$$P_1, P_2, \ldots, P_{99}$$

**P₅₀** = mediana

---

## Ejemplo de interpretación

Si un estudiante está en el **percentil 80**, significa que obtuvo un puntaje superior al 80% de los demás estudiantes.

---

# Cálculo de cuartiles en R

```r
datos <- c(10, 12, 15, 18, 20, 22, 25, 28, 30)

quantile(datos, probs = c(0.25, 0.5, 0.75))

# Resultado:
# 25%   50%   75%
# 15    20    25
```

---

# Rango intercuartílico (IQR)

$$IQR = Q_3 - Q_1$$

Mide la dispersión del 50% central de los datos.

- Es robusto frente a valores extremos.

---

## Ejemplo

Si $Q_1 = 15$ y $Q_3 = 25$:

$$IQR = 25 - 15 = 10$$

El 50% central de los datos tiene un rango de 10 unidades.

---

# Identificación de valores atípicos

Se usa el IQR para detectar **outliers**.

Un valor es atípico si:

$$x < Q_1 - 1.5 \cdot IQR$$
$$\text{o}$$
$$x > Q_3 + 1.5 \cdot IQR$$

---

## Ejemplo

$Q_1 = 15$, $Q_3 = 25$, $IQR = 10$

$$\text{Límite inferior} = 15 - 1.5 \cdot 10 = 0$$
$$\text{Límite superior} = 25 + 1.5 \cdot 10 = 40$$

Cualquier dato menor a 0 o mayor a 40 es un **outlier**.

---

# Boxplot (diagrama de caja)

Representa gráficamente:

- Q₁, Q₂, Q₃
- Valores mínimos y máximos
- Outliers

Es muy útil para visualizar la dispersión y simetría de los datos.

---

# Ejemplo de boxplot

![Boxplot](https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Boxplot_vs_PDF.svg/400px-Boxplot_vs_PDF.svg.png)

---

# En R

```r
datos <- c(10, 12, 15, 18, 20, 22, 25, 28, 30, 100)

boxplot(datos,
        main = "Diagrama de caja",
        ylab = "Valores",
        col = "lightblue")
```

---

<!-- _class: lead -->
# 05
# Medidas de Dispersión
## ¿Qué tan dispersos están los datos?

---

# ¿Por qué medir la dispersión?

Dos conjuntos de datos pueden tener la **misma media** pero diferir mucho en cómo están distribuidos.

- La dispersión indica la **variabilidad** de los datos.
* (Que tan cercanos son los datos entre si)

---

## Ejemplo

**Conjunto A:** 10, 12, 15, 18, 20
**Conjunto B:** 5, 10, 15, 20, 25

Ambos tienen media = 15, pero B es más disperso.

---

# Principales medidas de dispersión

- **Rango**
- **Varianza**
- **Desviación estándar**
- **Coeficiente de variación**
* Veamos en que consiste cada uno...

---

# Rango

$$\text{Rango} = \text{Máximo} - \text{Mínimo}$$

Fácil de calcular, ero muy sensible a valores extremos.
- "Nuestros datos van de x valor a y valor."

---

## Ejemplo

**Datos:** 10, 15, 20, 25, 100

$$\text{Rango} = 100 - 10 = 90$$

Un solo valor extremo aumenta mucho el rango.

---

# Varianza

Mide la dispersión promedio respecto a la media.

**Para una población:**

$$\sigma^2 = \frac{\sum (x_i - \mu)^2}{N}$$

**Para una muestra:**

$$s^2 = \frac{\sum (x_i - \bar{x})^2}{n - 1}$$

---

## ¿Por qué se eleva al cuadrado?

Al elevar al cuadrado:

- Las desviaciones no se cancelan.
- Fuerza al positivo todas las desviaciones.
- Se penalizan más las desviaciones grandes.

---

## Ejemplo de cálculo

**Datos:** 10, 15, 20

$$\bar{x} = \frac{10 + 15 + 20}{3} = 15$$

$$s^2 = \frac{(10-15)^2 + (15-15)^2 + (20-15)^2}{3-1}$$
$$= \frac{25 + 0 + 25}{2} = \frac{50}{2} = 25$$

---

# Desviación estándar

Raíz de la varianza.

$$\sigma = \sqrt{\sigma^2}$$
$$s = \sqrt{s^2}$$

Se expresa en las mismas unidades que la variable.

---

# Interpretación formal

- Si $s$ es pequeña → alta concentración alrededor de la media.

- Si $s$ es grande → alta variabilidad.

La media es más representativa cuando la dispersión es baja.

---

# Desviación intercuartílica

$$DI = \frac{Q_3 - Q_1}{2}$$
$$ \text{o}$$
$$DI = \frac{RIC}{2}$$

- Mide dispersión del 50% central.

- No depende de valores extremos.

---

# Desviación estándar y forma de la distribución

La desviación estándar no solo mide dispersión.

Cuando la distribución es aproximadamente normal, determina la forma completa de la curva.

(Hablando sobre la forma de la distribución)
Media → fija el centro. 
Desviación estándar → fija la amplitud.

---

# Distribución normal (Campana de Gauss)

Modelo teórico de distribución simétrica.

- Simétrica respecto a la media
- Media = Mediana = Moda
- Área total bajo la curva = 1

Representa fenómenos naturales donde los valores se concentran alrededor del promedio.

---

# La magia de la campana de Gauss (para los curiosos)

Muchas cosas se aproximan a una distribución normal, pero no porque la naturaleza "prefiera" esa forma.

* Sucede por una razón matemática.

---

# ¿Por qué aparece tanto?

Cuando una variable es el resultado de:

- Muchos efectos pequeños  
- Independientes  
- Que se suman  

El resultado tiende a tomar forma de campana.

---

# Ejemplos comunes de distribución normal

Algunos casos donde suele aproximarse a una campana de Gauss:

- Altura de personas en una población
- Peso de adultos en un grupo homogéneo
- Calificaciones en un examen grande
- Errores de medición
- Presión arterial en adultos

En todos estos casos intervienen muchos pequeños factores independientes.


---

# ¿Por qué es tan útil?

Porque con solo dos parámetros:

- Media → fija el centro  
- Desviación estándar → fija la amplitud  

queda completamente determinada la distribución.

---

# Pero no todo es normal

Muchos fenómenos reales son asimétricos o tienen valores extremos frecuentes.

La campana aparece bajo condiciones específicas, no en todos los casos.

* Retomemos...
---

# Efecto de la dispersión

Si $s$ es pequeña:
Curva angosta y alta.

Si $s$ es grande:
Curva más ancha y achatada.

Mayor dispersión →
menor concentración alrededor de la media.

---

# Regla empírica

En una distribución normal:

- 68% de los datos están en $\bar{x} \pm 1s$
- 95% están en $\bar{x} \pm 2s$
- 99.7% están en $\bar{x} \pm 3s$

La desviación estándar permite
cuantificar la concentración de los datos.

---

# Conexión conceptual

En distribuciones normales:

- La media describe la tendencia central.
- La desviación estándar describe la dispersión.
- Ambas juntas describen completamente la distribución.


---
# Coeficiente de variación

Medida relativa.

$$CV = \frac{s}{\bar{x}} \cdot 100$$

Permite comparar distribuciones con distintas unidades.

Si el CV es mayor → mayor variabilidad relativa.

---

# Idea clave

La tendencia central indica posición.

La dispersión indica estabilidad.

Ambas deben analizarse juntas.

---
<!-- _class: lead -->

# 06
# Otras medidas estadísticas 
# Asimetría y Curtosis.

## Además de medir tendencia central y dispersión, también podemos describir la forma de la distribución.

---
# Asimetría

Mide el grado de simetría de una distribución.

Indica si los datos se inclinan hacia la derecha o hacia la izquierda.

---
# Interpretación de la asimetría

- Asimetría = 0 → distribución simétrica
- Asimetría > 0 → sesgo hacia la derecha
- Asimetría < 0 → sesgo hacia la izquierda

La distribución normal tiene asimetría igual a 0.

---
# Fórmula del coeficiente de asimetría

Una forma común de medirla es:

$$
g_1 = \frac{\frac{1}{n} \sum (x_i - \bar{x})^3}{s^3}
$$

Donde:

- $\bar{x}$ es la media
- $s$ es la desviación estándar
- $n$ es el número de datos

---
# ¿Por qué se eleva al cubo?

En la fórmula:

$$
g_1 = \frac{\frac{1}{n} \sum (x_i - \bar{x})^3}{s^3}
$$

Se eleva al **cubo** la desviación respecto a la media.

- Potencias pares eliminan el signo.
- Potencias impares conservan el signo.
- El cubo es la menor potencia impar que permite medir intensidad.

---

# Idea clave

El cubo permite:

1. Distinguir dirección del sesgo.

1. Dar mayor peso a valores extremos.

1. Detectar si predominan desviaciones positivas o negativas.

* Si predominan desviaciones positivas → hay valores altos extremos → sesgo a la derecha.

* Si predominan desviaciones negativas → hay valores bajos extremos → sesgo a la izquierda.


---
# Representación gráfica de la asimetría

![Imagen de distintos tipos de asimetria y simetria](data:image/jpeg;base64,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)
- Distribución simétrica
- Asimetría positiva
- Asimetría negativa

La asimetría describe hacia dónde se extiende la cola.

---
# Curtosis

Mide el grado de concentración de los datos alrededor de la media.

- Indica qué tan "picuda" o "achatada" es una distribución.

---
# Fórmula del coeficiente de curtosis

Una forma común es:

$$
g_2 = \frac{\frac{1}{n} \sum (x_i - \bar{x})^4}{s^4}
$$


En la distribución normal, la curtosis es 3.

---
# Tipos de curtosis

- Mesocúrtica → similar a la normal
- Leptocúrtica → más picuda y concentrada
- Platicúrtica → más achatada

Muchas veces se usa:

- Exceso de curtosis = g₂ − 3
* Se resta 3 porque se toma la normal como referencia. 

---

**Sobre el exceso de curtosis:**

- Exceso = 0 → comportamiento similar a la normal (mesocúrtica)
- Exceso > 0 → más apuntada y con colas más pesadas (leptocúrtica)
- Exceso < 0 → más achatada y con colas más livianas (platicúrtica)

---
# Representación gráfica de la curtosis

![Imagen de comparacion de kurtosis](https://miro.medium.com/v2/resize:fit:240/format:webp/0*G6s35dRemv1Ilfqj.jpg)
- Mesocúrtica (normal)
- Leptocúrtica
- Platicúrtica

La curtosis describe el grado de concentración y el peso de las colas.

---
# Conexión con la distribución normal

Distribución normal:

- Asimetría = 0
- Curtosis = 3

Sirve como modelo de referencia para comparar otras distribuciones.

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

# La estadística como lenguaje universal

**No es solo matemática.**

Es el lenguaje que permite a todas las ciencias hablar con datos.

Desde la medicina hasta la informática, desde la economía hasta la física.

---

# Más allá de los números

Los conceptos vistos no son fórmulas aisladas.

Son herramientas para:

- Resumir y organizar información.
- Describir el comportamiento de los datos.
- Comparar distribuciones.
- Extraer conclusiones basadas en evidencia.

En estadística descriptiva no buscamos predecir ni validar hipótesis,
sino **comprender y comunicar claramente la información contenida en los datos**.


---

# Reflexión final

**La estadística no elimina la incertidumbre.**

**Nos enseña a cuantificarla, comprenderla y trabajar con ella.**

En un mundo lleno de datos, esta es una habilidad invaluable.

---
<!-- _class: lead -->

# Gracias

**Estadística I**
UNM - FCEQyN - 2025

*"En Dios confiamos, todos los demás deben traer datos."*
— W. Edwards Deming
