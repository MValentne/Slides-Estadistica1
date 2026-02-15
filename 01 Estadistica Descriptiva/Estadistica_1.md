---
marp: true
theme: academic 
math: katex
paginate: true
---
# Estadistica I
# UNM - FCEQyN - 2025
## Valentino Mende
---
<!-- _class: lead -->
# 00
# Introduccion a la Estadistica
## De datos a prediccion
---
# Origen
La palabra estadistica surge de la nocion del estado; de la recoleccion, organizacion, conservacion y tratamiento de datos DEL ESTADO.
- Era una herramienta de gobierno para conocer la situacion del estado.
* Hoy en dia ha evolucionado a ser una **metaciencia**.
* Aporta herramientas fundamentales a todas las otras ciencias.
---
La estadistica se desarrollo a la par que la matematica, aprovechando en particular los avances en probabilidad.
- Probabilidad --> Propone modelos matematicos para modelar la aleatoreidad.
- Es la base para la estadistica inferencial. (mas de esto despues)
- Estadistica --> Aprovecha tales modelos para entender datos.
- El uso de modelos y calculo probabilistico en muchas ocasiones nos ayuda a comprender aquello en lo que la simple intuicion seria erronea.
* Paradoja del cumpleanos...
---
# Paradoja del cumpleanos
Cual es la probabilidad de que una persona coincida en cumpleanos con otra en un grupo de 23 personas?
* "Yo creo que es practicamente imposible..."
* Resulta que es bastante probable!
### Desarrollo:
* Para 2 personas, la probabilidad es de P(c_1 = c_2)
* Para 3 personas, P(c_1 = c_2, c_1 = c_3, c_2 = c_3)
* Un posible problema de conteo?? (mas de esto adelante)
---
Para ver cuantas posibilidades distintas (cuantos escenarios) existen, podemos verlo como un problema de conteo. 
Visto de esta forma:
* Si tenemos un grupo de 20 personas, queremos ver cuantas concordancias de 2 personas pueden haber, cuantas combinaciones pueden formar!
* 20C2 --> 20 personas en eleccion por par
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
- Economia, 
- Finanzas 
- y en nuestro caso de interes, **Informatica**.
* Un ejemplo claro aplicado al campo, la **Teoria de la Informacion**!
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
# La Estadistica
## Nos adentramos un poco mas...
---
Al hablar de estadistica nos llega a la mente un conjunto de datos a estudiar, usualmente llamado "dataset"
- Una representacion ordenada y sistematica de los datos
* Hoy en dia podemos extraer un dataset de practicamente cualquier topico.
* vease [Google Dataset Research](https://datasetsearch.research.google.com/)
* vease [TidyTuesday](https://github.com/rfordatascience/tidytuesday?utm_source=chatgpt.com)
---
Para ciertos campos, la estadistica resulta ser la herramienta principal para dar luz y obtener resultados.
- Esta es mas visible en las ciencias sociales.
- Esta fuertemente ingtegrada en la estructura de otros campos, tales como:
* Fisica
* Biologia y Medicina
* Ciencia de datos / Machine learning
* Economia
* Etc.
--- 
La estadistica se encarga de los metodos y procedimientos para recoger, clasificar, resumir, hallar regularidades y analizar los datos; siempre y cuando la variabilidad de incertidumbre de tales datos correspondan a la naturaleza propia de estos y no de algun factor externo. 
* **Ejemplifiquemos...**
---
Tiramos 100 veces una moneda...
* Algunas veces sale cara, algunas veces sale cruz.
* Es la naturaleza de la moneda, por lo que podemos emplear estadistica.

Nos subimos a una balanza mal calibrada, la medicion es incorrecta por 5kg...
* La balanza tiene un problema, por lo que no se aprecia la naturaleza de la balanza.
* No empleamos estadistica. 
---
# La Estadistica Descriptiva
Se encarga de los metodos y procedimientos para:
- Recoger
- Clasificar
- Resumir
- Hallar regularidades
- Analizar datos
---
# La Estadistica Inferencial
Obtiene conclusiones a partir de tales datos analizados previamente, con la finalidad de generar predicciones con cierto grado de confianza.

---
## En vista general...

La estadistica entonces dejo de ser una tecnica centrada en los estados para convertirse en una herramienta imprescindible de todas las ciencias.

La estadistica hace inferencias sobre una poblacion, partiendo de una muestra significativa de esta.

---

## Ya hablamos un poco sobre la estadistica, pero cabe concretar conceptos.

---
# Importancia y definicion
La estadistica es un conjunto de tecnicas que, partiendo de la observacion de un fenomeno, nos permite conseguir conclusiones utiles. 
* La estadustuca descriptiva se encarga de la recoleccion, clasificacion y descripcion de datos muestrales o poblacionales para su interpretacion y analisis
* La estadistica inferencial (o matematica) se basa en la prediccion. Desarrolla modelos teoricos que se ajustan a una determinada realidad con cierto grado de confianza. 
* Cabe aclarar que estas ramas no son opuestas...
* Se complementan.
---

<!-- _class: lead -->
# 01
# Conceptos Fundamentales
## Entramos en contexto, ahora vamos a los detalles.
--- 
# Etapas del metodo estadistico
1. **Planteamiento del problema**: Que se estudiara y por que se tiene que estudiar? Recurrimos a la revision bibliografica del tema (ver investifaciones previamente realizadas).
2. **Fijacion de objetivos**: Fijamos metas y objetivos; hasta donde se desea presupuestar, hasta donde queremos llegar. 
3. **Formulacion de hipotesis**: Una explicacion provisional de los hechos y el objeto de estudio. Una hipotesis estadistica debe ser susceptible a probar su veracidad. (Hipotesis nula y alternativa son temas de los que se hablara a futuro.)
---
4. **Definicion de la unidad de observacion y de la unidad de medida**: La unidad de observacion corresponde a cada uno de los elementos de la poblacion observada, mientras que la unidad de medida habla de la medida en la que se analizan las variables estudiadas. (metros, kilos, litros...)
5. **Determinacion de la poblacion y de la muestra**: En notacion conjuntista diriamos que la poblacion es el universo (nuestro dataset entero), mientras que la muestra es un subconjunto de tal universo; un subconjunto significativo, representativo de toda la poblacion (usualmente optamos por esta ultima, estudiamos un pedazo para entender el todo.)
6. **La recoleccion**: En pocas palabras, la encuesta. Descubrir donde esta la informacion, como y a que costo conseguirla. Se obtiene una aproximacion de la variabilidad de poblacion. 
---
7. **Critica, clasificacion y ordenacion**: Se depuran las respuestas falsas o inutilizables, aquellas que estan fuera de lugar para lo que queremos estudiar. Dejado de lado el material desechado, se clasifica y ordena la informacion (usualmente se emplea computo en esta etapa).
8. **La Tabulacion**: Se crea una tabla para simplificar la comprension de la informacion a quien la este analizando. Es de suma importancia la inclusion de elementos como un titulo adecuado, subtitulos internos y cuantificacion de las variables, y notas de pie de cuadro que otorguen claridad o creditos a quien corresponda.
9. **La presentacion**: Se trabaja en el informe, se presenta de la forma adecuada. No deseamos redundancia; graficos y tablas que no proporcionen informacion relevante, esto solo es confuso. 
--- 
10. **El analisis**: Es donde se cristaliza la investigacion. Buscamos establecer y redactar las conclusiones definitivas. Se determinan los parametros y estadisticos muestrales para las estimaciones e inferencias sobre la poblacion.	
11. **Publicacion**: "Toda conclusion es digna de ser comunicada en un auditorio". Buscamos dar a luz nuestra investigacion. Es posible que otros investigadores o estudiosos esten interesados en nuestro trabajo.
---
# Conceptos clave
- **Unidad de analisis**: Un elemento de la poblacion/universo que se esta estudiando
- **Poblacion o universo**: Representa un conjunto de todas las unidades de analisis que conforman el objeto de estudio. Se representa con (N).
- **Muestra**: Subconjunto significativo de la poblacion. Se representa con (n).
- **Parametro**: Cualquier funcion (digase, funcion estadistica como media aritmetica) sque determine una caracteristica numerica de la poblacion.
---
- **Estadistico/Estimador**: Caracteristica numerica de una muestra (Nuevamente una funcion, esta vez aplicada a un subconjunto).
- **Variables**: Propiedades, caracteristicas, cualidades... de los elementos de una poblacion. Se dividen en:
* Cuantitativas: discretas en caso de que sea contado en valores enteros, continuas en caso de requerir medidas intermedias entre valores (fraccionarias).
* Cualitativas: nominales si no siguen un criterio u orden, y ordinal si es que si lo siguen.
---

<!-- _class: lead -->
# 02 
# Distribucion de frecuencia
## Agrupando datos...

---
# Sobre la distribucion de frecuencias
Habla de agrupaciones de datos segun su clase, a esta clase se le denomina modalidad del caracter estadistico.
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
En el esquema anterior se muestra una organizacion de datos mediante una tabla.
El objetivo es acomodar el dataset de forma util para simplificar el analisis de la informacion contenida. 
* **Frecuencia absoluta**: Cantidad de veces que una modalidad ha sido observada (digase el numero de veces que aparece dicho valor de la variable)
* se representa con f[i].
* **Frecuencia relativa**: Tiene relacion con la cantidad total del tamano de muestra.
* digase: _h[i] = Fr = fi/N_, que da de resultado un valor entre [0,1].
* Al multiplicar por 100, pasa a ser una frecuencia porcentual.
---
- **Frecuencia absoluta acumulada**: Es la suma progresiva de las frecuencias absolutas de cada clase o intervalo. 
* En pocas palabras, dice cuantos datos hay hasta tal modalidad.
* Cabe especificar que la variable debe ser cuantitativa o cualitativa ordenable para que esta tenga sentido.
---
# Intervalos de clase
Un intervalo se usa cuando una variable es cuantitativa continua o los datos son discretos, pero muy numerosos. 
Llamaremos amplitud, longitud o ancho del intervalo a la diferencia entre el extremo inferior del intervalo y el inferior del siguiente intervalo.

---
**Ejemplo:**

|   |   limite inferior |   limite superior |
|:---:|:---:|:---:|
| [10,15)  |   10   |               15
| [15,20)  |   15   |               20
|[20,25)   |  20    |              25
| [25,30)  |   25   |               30
---

## Algunas ideas clave
**Marca de clase**: Punto medio de cada intervalo, digase: [15,20], Marca de clase = (15+20)/2 = 17.5
- Surgen 3 preguntas de interes:
1. Cuantas clases deben usarse?
2. Cual debe ser la amplitud de clase?
3. En que valor debe empezar la primera clase?

--- 
///////////////// Aplicar LaTeX

1. Si usamos pocas clases, perderemos informacion; y si usamos demasiadas puede que alguna clase no tenga valor. Entonces cuantas clases debemos usar?
* Usamos Sturges. C = cantidad de clases; C = 3.32 x log(n) + 1 
 
---
2. Cual debe ser la amplitud? Esta se encuentra al usar el rango de la muestra (R).
* R = diferencia entre la medida mayor y la menor de la muestra
* R = U(limite superior) - L(limite inferior)
* Amplitud = A = R/U 
---
3. En que valor empieza la primera clase?
* Respuesta simple, en el limite inferior de la muestra (L).
---
<!-- _class: lead -->
# 03
# Graficos estadisticos
## Representando informacion...

---
# Graficos para v.Cualitativas
## Diagrama de barras
![imagen de diagrama de barras](data:image/jpeg;base64,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)
* Alturas proporcionales a las frecuencias
* Aplicable a cuantitativas discretas
* Las barras estan separadas
---
## Diagramas de sectores
(El famoso diagrama de pastel)
![Imagen de diagrama de sectores](data:image/png;base64,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)
* No usarlo con variables ordinales (no tendria ningun orden).
* El area de cada sector es proporcional a su frecuencia.
---
## Pictogramas
![Imagen de un pictograma](data:image/jpeg;base64,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)
* Son bastante sencillos de asimilar visualemente.
* Cada figura corresponde a cierta frecuencia de la variable.
---
# Graficos para v.Cuantitativas
Son diferentes en funcion que la variable sea discreta o continua, con frecuencia absoluta o relativa.
* Previamente mencionamos que un diagrama de barras puede ser utilizado para variables cuantitativas discretas. 
---
## Histogramas 
(Para variables continuas)
![Imagen de un histograma](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAPsAAADJCAMAAADSHrQyAAAAq1BMVEX///+t2ObX19eMjIwAAACp0+HR0dHj4+M+TlOr1uRKSkqx3u1eWllDVFmXvclGV12hydZJXWQ4R0s8UllVZ2xYWlvw7++Osb35+flfX1/s6+re3NzCwcFUZGpee4VsbGy2s7Kdm5pSbXaDprJ2dnZng4xNVVfKyspzc3OAgICkpKSVlZV9nKaKioq8vLyurq47OzsaLTEgICBEPz4XHyInKixNVVguOz9NTU2yVdJnAAAFMElEQVR4nO3da3uiOBgG4Bi3Qeu4Om5Jw6EFtkwxuMDszs5M//8vW88dgtvQKojmefrFi+utvHflYE1AQhAEQcxKmPUNCa3Y7YSakbBfsTuija2rA6EH7PwMfZwjsJcCe8uxPDXNd9EV+9+PapzG19kV+x+9kZJPja+zM/abXjmwNxrYS4G95cB+Pvv2fxjz7EzkQbHWm2eXVmal63/mzbP3Iyn6bPXIPLvLcr7c5pmUt8bZWZCS3COced+sxtdazVntmRcuwvX+fmucfZGT/B9D7SIhJHFXj8yzvwb2lgM77LDD3mRgLwX2lgM77LDD3mRgLwX2lgM77LDD3mRgLwX2lnNeO+d8MwBvnj1xsixbj0KaZ5cuIWmyemSePczCYuUXBtqJxehyf09s56tx9tCWvDB0HFYKKlND7WlEqKnj78Rb7vKGnuNeA3uj8UM1E1PsfPakZmyM/fPNqAztDQyyK9Ih7LDDDnuTgb0U2JsM7LDDDjvssMPeaGAvBfYmA3t37IKIZHMhrHn2Po/7sqVrA7tmlzQiYUvj712z5/PADSzCqWWefdnR8ocwJ2h+/L1rdj+KooWh+zt9yfO8pXHYrtlJsrvVg4H2fWBvMrDDDjvssMNutP2br+bUfXXX/u8XNc8nbqO79pl6s96RfeI2OmzvqUtgP11gL+VYu1BSrbhWu2WPf5QzW6g112qnd+rheTpXX/prtXt3as+/x7C/BnbYYYcd9vbtIsnZKcbfL9Ee9cM09laPzLPLZYPFCcbfD9nVmq7ZaSxlKojlJ8fdh/yA3c6VD5/Cjtm3XzfhRelx4+8H7N/VD58eO2ZPg3gerNUn3+Yn6ndFTStXQZ7X7toJZeuX/vR21dU1O7F2R2MD7fvA/tHADjvssMMOO+ywww477LDDDjvssJ8wsJcC+0fTpJ2rOTCH6x25JPt3R4mdHdPpRdkHo2EpveGPYzq9MLv6W8fNrIZ9k+2FkebZQ5G+LLo9HteYXVoZKRjxFtF7xqBFESmRDxdodxweM+Im7D1zD+j4vnyP3fsvk8uzE55wf/3gPds8e1D6Gd1fon2fo+w92GFv3H7W93Xnft25q4Tre74O+83PP9X8NMY+UK9PGQ6Msc+qfw3YYYcddthhhx32j9upOfaivygn/myKnY3Vr4F6HBtjv1uta7++UW/0ZJj913Zgh/2q7B4rhxaVT6QvwO4yNTvfG3bv+U7JbHJ5djFXFQ/PQmtPKlv4Xxdo55/UnqdjY+296QT2X8fjdhdGHmVvdTzuVHbfjueSK3ZlfsvSrix5GveUJfeTobJkaVeWLO1K0c1AXTKaDdUlA3Vd05naz/SAvfJbe/tuqtLqAv0wISwIbp1gHfu3a83GFzjF1p4Gi2xuEe5Zu4QBrZwaK2d8R1vDcifR1rAXfQ190a8rudXX+DbdCvfT8wRTxrKSyr0aqmGBvsaa62uIU6OmxrxK8aKv4Y5+SqLl65/HrVHDa9SQsEZNoS8RNZ5H5MdNx0SuOJzqR7M5q7EBWdoaQWs8TY3B9Trt1GERJ9UegTwn0s/nTbSz1sR8oT8g0q+JroTbkdTinbTOAZpq7Zzrj5qCBTo769c40DOptQuXONpPmS0v0LRs+RYpNEWez7nUHMVpzonU9eNHpHJTy2oWWjvhca6tIWHsvl1g+bQgmxtc/W8835u/XbGxxzo7lXVO8Hq70L0Sq6SkRtXyrZ6uhDpSv4ORVPN3JiQKapy8C6qrsByZaddVg0W2d3lqJ22+3cBbGwRBDMx/YtkStwtxHG0AAAAASUVORK5CYII=)
* Las barras estan juntas.
* Representa la frecuencia o porcentaje en su area correspondiente. 
---
## Ojivas
Bastante similar a un histograma...
![Imagen de una ojiva](data:image/png;base64,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)

---

# Variables cuantitativas segun variables cualitativas
## Diagrama BoxPlot (Caja y bigotes)

Ampliamente utilizado en publicaciones cientificas, gran capacidad de representar la distribucion de la variable, valores centrales y datos extranos

- Resumen grafico de una distribucion.

- No muestra todos los datos.
* Muestra estructura.

---
# Boxplot
## Se basa en 5 valores

- Minimo
- Q1
- Mediana
- Q3
- Maximo
---
# Estructura
<img src="data:image/png;base64,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" width="500" alt="Description">

- La caja va de Q1 a Q3.
- La linea interna es la mediana.
- Los bigotes llegan a los extremos.

La caja contiene el 50% central.

---
# Rango intercuartil

$$RI = Q3 - Q1$$

Mide dispersion del 50% central.

---

# Valores atipicos

Se consideran atipicos los valores que cumplen:

$$x < Q1 - 1.5RI$$  
$$x > Q3 + 1.5RI$$

---
# Para que sirve

- Comparar distribuciones.
- Ver dispersion.
- Detectar asimetria.
- Identificar outliers.

---
# 05 
# Medidas de tendencia central
## Buscar un valor que represente al conjunto, un valor tipico y un valor central.

---

# Idea general

Las medidas de tendencia central reducen muchos datos a un solo numero.

Ese numero resume informacion clave del conjunto y representa su posicion central.

---
# Media aritmetica

**Promedio.**

$$\bar{x} = \frac{\sum x_i}{n}$$

- Suma de los datos dividida por la cantidad.

--- 

## Caracteristicas de la Media

- Usa todos los datos.
- Es sensible a valores extremos.
- Es unica.
- Representa el centro de gravedad de la distribucion.

Si cambian los extremos, la media cambia.

---
# Mediana

**Valor central** cuando los datos estan ordenados.

- Si $n$ es impar: es el valor del medio.
- Si $n$ es par: promedio de los dos centrales.

---
## Caracteristicas de la Mediana

- Divide al conjunto en dos partes iguales.
- No se ve afectada fuertemente por extremos.
- Es adecuada en distribuciones asimetricas.

---
# Moda

Valor que mas se repite.

Puede haber:
- Una moda (unimodal)
- Dos modas (bimodal)
- Mas de dos (multimodal)

- Puede no existir.

---
## Comparacion

Media → sensible a extremos.  
Mediana → robusta.  
Moda → frecuencia maxima.

No siempre coinciden.

---
## Eleccion adecuada

Depende de la distribucion.

Simetrica → media.  
Asimetrica → mediana.  
Datos cualitativos → moda.

---
# Otras medidas posicionales

- Surgen como generalizacion de la mediana.
- Dividen la distribucion en partes iguales.
- Permiten ubicar datos segun su posicion relativa.

---
## Cuartiles

Dividen la distribucion en **4 partes iguales**.

- $Q_1$ → 25%
- $Q_2$ → 50% (es la mediana)
- $Q_3$ → 75%

Indican como se distribuyen los datos en cuatro secciones.

---
## Deciles

Dividen la distribucion en **10 partes iguales**.

- $D_1, D_2, ..., D_9$

Cada uno representa un 10% acumulado.

---
## Percentiles

Dividen la distribucion en **100 partes iguales**.

- $P_1, P_2, ..., P_{99}$

Generalizan a cuartiles y deciles.

Permiten analisis mas detallado de posicion.

---
# Posicion de un percentil

La posicion de un percentil $P_k$ se calcula como:

$$L = \frac{k}{100} \cdot n$$

Donde:

- $k$ → percentil buscado
- $n$ → cantidad de datos

Si $L$ no es entero,
se interpola entre posiciones.

---
# Calculo de cuartiles

Son percentiles especiales.

$$Q_1 = P_{25}$$  
$$Q_2 = P_{50}$$  
$$Q_3 = P_{75}$$

Se calcula la posicion
igual que cualquier percentil.

---
# Calculo de deciles

Son tambien percentiles.

$$D_k = P_{10k}$$

Ejemplo:

$$D_1 = P_{10}$$  
$$D_5 = P_{50}$$  
$$D_9 = P_{90}$$

---
# Datos agrupados en intervalos

Cuando los datos estan agrupados:

Se usa la formula general:

$$P_k = L_i + \left( \frac{\frac{k}{100}n - F_{anterior}}{f_i} \right) \cdot c$$

Donde:

- $L_i$ → limite inferior del intervalo
- $F_{anterior}$ → frecuencia acumulada anterior
- $f_i$ → frecuencia del intervalo
- $c$ → amplitud del intervalo

---
# Porcentaje por debajo o por encima de un valor

A veces no buscamos un percentil. Buscamos el porcentaje de datos que estan por debajo o por encima de un valor determinado.

Es el problema inverso.

- Dado un valor en X, queremos el porcentaje en Y.

---
## Formula general

$$
p = \left[ faa + \frac{f_i (P - L_i)}{c} \right] \frac{100}{N}
$$


- $p$ → porcentaje buscado.
- $P$ → valor dado.
- $faa$ → frecuencia acumulada anterior.
- $f_i$ → frecuencia del intervalo.
- $L_i$ → limite inferior del intervalo.
- $c$ → amplitud del intervalo.
- $N$ → total de datos.


---
# 06
# Medidas de dispersion
## Variabilidad respecto a una medida central

---

# Idea fundamental

La dispersion mide
que tan alejados estan los datos
respecto a un valor central
(generalmente la media).

Sin dispersion,
la media no tiene sentido descriptivo.

---
# Dispersión absoluta y relativa

**Absolutas**  
Se expresan en las mismas unidades que los datos.

**Relativas**  
Son proporciones o porcentajes.
Permiten comparar distribuciones distintas.

---
# Rango (R)

$$R = X_{max} - X_{min}$$

Mide la amplitud total.

Solo considera dos valores.
Muy sensible a extremos.

---
# Desviaciones respecto a la media

Se define el desvio individual:

$$d_i = x_i - \bar{x}$$

Propiedad importante:

$$\sum d_i = 0$$

Por eso se elevan al cuadrado
para medir dispersion real.

---
# Varianza

Poblacional:

$$\sigma^2 = \frac{\sum (x_i - \mu)^2}{N}$$

Muestral:

$$s^2 = \frac{\sum (x_i - \bar{x})^2}{n - 1}$$

Mide dispersion cuadratica promedio.

---
# Desviacion estandar

Raiz de la varianza.

$$\sigma = \sqrt{\sigma^2}$$
$$s = \sqrt{s^2}$$

Se expresa en las mismas unidades
que la variable.

---
# Interpretacion formal

Si $s$ es pequeño →
alta concentracion alrededor de la media.

Si $s$ es grande →
alta variabilidad.

La media es mas representativa
cuando la dispersion es baja.

---
# Desviacion intercuartilica

$$DC = Q_3 - Q_1$$

Mide dispersion del 50% central.

No depende de valores extremos.

---
# Desviacion estandar y forma de la distribucion

La desviacion estandar no solo mide dispersion.

Cuando la distribucion es aproximadamente normal,
determina la forma completa de la curva.

Media → fija el centro.
Desviacion estandar → fija la amplitud.

---
# Distribucion normal (Campana de Bell)

Modelo teorico de distribucion simetrica.

- Simetrica respecto a la media
- Media = Mediana = Moda
- Area total bajo la curva = 1

Representa fenomenos naturales
donde los valores se concentran
alrededor del promedio.

---
# Efecto de la dispersion

Si $s$ es pequeña:
Curva angosta y alta.

Si $s$ es grande:
Curva mas ancha y achatada.

Mayor dispersion →
menor concentracion alrededor de la media.

---
# Regla empirica

En una distribucion normal:

- 68% de los datos estan en $\bar{x} \pm 1s$
- 95% estan en $\bar{x} \pm 2s$
- 99.7% estan en $\bar{x} \pm 3s$

La desviacion estandar permite
cuantificar la concentracion de los datos.

---
# Conexion conceptual

En distribuciones normales:

La media describe la tendencia central.
La desviacion estandar describe la dispersion.
Ambas juntas describen completamente la distribucion.


---
# Coeficiente de variacion

Medida relativa.

$$CV = \frac{s}{\bar{x}} \cdot 100$$

Permite comparar
distribuciones con distintas unidades.

Si el CV es mayor →
mayor variabilidad relativa.

---
<!-- _class: lead -->
# Idea clave

La tendencia central
indica posicion.

La dispersion
indica estabilidad.

Ambas deben analizarse juntas.

---
# 07
# Otras medidas estadisticas 
# Asimetria y Kurtosis.

## Ademas de medir tendencia central y dispersion, tambien podemos describir la forma de la distribucion.

---
# Asimetria

Mide el grado de simetria de una distribucion.

Indica si los datos se inclinan
hacia la derecha o hacia la izquierda.

---
# Interpretacion de la asimetria

- Asimetria = 0 → distribucion simetrica
- Asimetria > 0 → sesgo hacia la derecha
- Asimetria < 0 → sesgo hacia la izquierda

La distribucion normal tiene asimetria igual a 0.

---
# Formula del coeficiente de asimetria

Una forma comun de medirla es:

$$
g_1 = \frac{\frac{1}{n} \sum (x_i - \bar{x})^3}{s^3}
$$

Donde:

- $\bar{x}$ es la media
- $s$ es la desviacion estandar
- $n$ es el numero de datos

Se basa en el tercer momento centrado.

---
# Representacion grafica de la asimetria

[AQUI INSERTAR GRAFICO:
- Distribucion simetrica
- Asimetria positiva
- Asimetria negativa]

La asimetria describe hacia donde se extiende la cola.

---
# Curtosis

Mide el grado de concentracion
de los datos alrededor de la media.

Indica que tan "picuda" o "achatada"
es una distribucion.

---
# Formula del coeficiente de curtosis

Una forma comun es:

$$
g_2 = \frac{\frac{1}{n} \sum (x_i - \bar{x})^4}{s^4}
$$

Se basa en el cuarto momento centrado.

En la distribucion normal,
la curtosis es 3.

---
# Tipos de curtosis

- Mesocurtica → similar a la normal
- Leptocurtica → mas picuda y concentrada
- Platicurtica → mas achatada

Muchas veces se usa:

Exceso de curtosis = g₂ − 3

---
# Representacion grafica de la curtosis

[AQUI INSERTAR GRAFICO:
- Mesocurtica (normal)
- Leptocurtica
- Platicurtica]

La curtosis describe el grado de concentracion
y el peso de las colas.

---
# Conexion con la distribucion normal

Distribucion normal:

- Asimetria = 0
- Curtosis = 3

Sirve como modelo de referencia
para comparar otras distribuciones.

---
# Cierre conceptual

Tendencia central → donde se ubican los datos.
Dispersion → cuanto se separan.
Asimetria → hacia donde se inclinan.
Curtosis → como se concentran.

Juntas describen completamente
la forma de una distribucion.












