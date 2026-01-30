---
marp: true
theme: gaia
math: katex
paginate: true
---
# Estadistica I
# UNM - FCEQyN - 2025
---
<!-- _class: lead -->
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
