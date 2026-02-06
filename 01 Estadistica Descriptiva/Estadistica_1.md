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
























