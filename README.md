# Breast Cancer Wisconsin (Diagnostic) ♥ Prueba Final (OPCIÓN A)


# Descripción
El proyecto presenta 3 modelo que permite evaluar los datos para identificar si un paciente tiene o no cáncer. Para este estudio se utilizo los métodos: Logistic Regression, Decision Trees y KNeighborsClassifier

# Dataset
Breast Cancer Wisconsin (Diagnostic)
https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+%28Diagnostic%29

1. Número de instancias: 569

2. Número de atributos: 32 (ID, diagnóstico, 30 características de entrada de valor real)

3. Información de atributos

1) número de identificación
2) Diagnóstico (M = maligno, B = benigno)
3-32)

Se calculan diez características de valor real para cada núcleo celular:

a) radio (media de las distancias del centro a los puntos del perímetro)
b) textura (desviación estándar de los valores de la escala de grises)
c) perímetro
d) área
e) suavidad (variación local en longitudes de radio)
f) compacidad (perímetro ^ 2 / área - 1.0)
g) concavidad (severidad de las porciones cóncavas del contorno)
h) puntos cóncavos (número de porciones cóncavas del contorno)
i) simetría
j) dimensión fractal ("aproximación a la línea de costa" - 1)

Varios de los documentos enumerados anteriormente contienen descripciones detalladas de
cómo se calculan estas características.

La media, el error estándar y el "peor" o mayor (media de los tres
valores más grandes) de estas características se calcularon para cada imagen,
resultando en 30 características. Por ejemplo, el campo 3 es Radio medio, campo
13 es Radius SE, el campo 23 es Worst Radius.

Todos los valores de características se recodifican con cuatro dígitos significativos.

4. Valores de atributos faltantes: ninguno

5. Distribución de clases: 357 benignos, 212 malignos

# Herramientas
IDE:Jupyter Notebook
Lenguaje de programación: Python
Archivo con la data: fashion-mnist_train.csv

# Análisis
1. RECOLECCIÓN DE DATOS
BDD:Breast Cancer Wisconsin
2. LIMPIEZA DE DATOS
- Se verificó si tienen el tipo de datos correcto en la BDD
- Se verificó si existen registro NAN
- Se eliminó la cabecera
3. PROCESAMIENTO DE DATOS
- Se importan las librerias como pandas, numpy, matplotlib, seaborn, sklearn
- Se comparó entre las dos variables de diagnostico
- La correlación de conjuntos de variables con sus respectivos diagnósticos a través de gráficos de correlación cruzada identifica qué variables tienen el mayor impacto en el entrenamiento del sistema.
- Se evidencia la relaciónn porcentual que existe entre cada variable, la cual, con esta gráfica se pueden separar los atributos que mayor importancia tienen en el Data-Set, entre estos atributos se encuentran : radius mean con 73 %,perimeter mean con 74 %, area mean con 71 %, concavity mean con 70 % y radius worst con 78 %. 
- Se entrenó los modelos con un preproceso, en este caso la columna de diagnosis pasó de tener las letras M y B a los números 1 y 0 respectivamente. 
- Para efectos de demostrar el funcionamiento de los Modelos de Machine Learning aplicados al diagnostico de cáncer de mama se va a realizar una prueba con variables de dos pacientes. El primer paciente tiene un diagnostico beningno y el paciente dos con un diagnostico maligno; se toman los valores de la columna 2 a la columna 31.
- Se asignan los datos de la columna 2 a la columna 31 en la variable X y los datos de la columna 1(diagnosis) en la variable Y. Luego se utiliza la función train test split de la librería model selection de sklearn para asignar el 75 % de los datos para que los modelos aprendan y el 25 % para comprobar la efectividad de los mismos.
# Resultados por Modelo
- Logistic Regression
Una vez el modelo fue entrenado se obtuvo un valor de 0.9577464788732394 de precisión del aprendizaje del mismo.
Se evaluó el modelo con un error de training: 4.225352112676061 % y error de test: 4.1958041958041985 %.
Una vez el modelo fue entrenado, se realiza el diagnostico con los datos del paciente 1 el cual arroja un resultado benigno con una probabilidad del 0.999835523095546 y una probabilidad del 0.00016447690445393646 de malignidad.
Una vez el modelo fue entrenado, se realiza el diagnostico con los datos del paciente 2 el cual arroja un resultado maligno con una probabilidad del 9.838252341687337e-07 y una probabilidad del 0.9999990161747658 de benignidad.
- KNN
Una vez el modelo fue entrenado se obtuvo un valor de 0.9413145539906104 de precisión del aprendizaje del mismo.
Se evaluó el modelo con un error de training: 5.868544600938963 % y error de test: 6.2937062937062915 %.
Una vez el modelo fue entrenado, se realiza el diagnostico con los datos del paciente 1 el cual arroja un resultado benigno con una probabilidad del 1.0 y una probabilidad del 0.0 de malignidad.
Una vez el modelo fue entrenado, se realiza el diagnostico con los datos del paciente 2 el cual arroja un resultado maligno con una probabilidad del 1.0 y una probabilidad del 0.0 de benignidad.
- Decision Trees
Una vez el modelo fue entrenado se obtuvo un valor de 1.0 de precisión del aprendizaje del mismo.
Se evaluó el modelo con un error de training: 0.0 % y error de test: 4.895104895104896 %
Una vez el modelo fue entrenado, se realiza el diagnostico con los datos del paciente 1 el cual arroja un resultado benigno con una probabilidad del 1.0 y una probabilidad del 0.0 de malignidad.
Una vez el modelo fue entrenado, se realiza el diagnostico con los datos del paciente 2 el cual arroja un resultado maligno con una probabilidad del 1.0 y una probabilidad del 0.0 de benignidad.
# Conclusiones
La precisión del modelo se determinó como la relación entre los diagnósticos realizados correctamente y el número total de diagnósticos, es decir, con qué frecuencia se clasificó correctamente a las personas con diagnósticos malignos o benignos. Para la validación del aprendizaje se utilizó el 25% de los datos, lo que corresponde a 144 de los 569 registros del dataset UW. 
Se puede observar que el modelo de árbol de decisión clasificó correctamente el 100% del total de datos utilizados para la validación con mayor precisión que los otros modelos seleccionados. Por otro lado, se puede observar que el modelo K-Nearest Neighbors (KNN) clasificó correctamente el 94,13% del total de datos utilizados para la validación, siendo la precisión más baja en comparación con los otros modelos seleccionados. Esto significa que el modelo de árbol de decisión es el más adecuado para el diagnóstico de cáncer de mama con datos obtenidos por el método de aspiración con aguja fina (FNA) trabajando solo con el training  y, por lo tanto, el modelo KNN es el menos adecuado para el diagnóstico de cáncer de mama con estos datos.
Por otro lado con el resultado de evaluación de test podemos concluir que el modelo más adecuado para aplicar es Logistic Regression siendo que es el menor porcentaje  4.1958041958041985 % y el menos indicado es el modelo KNN con un resultado de 6.2937062937062915 %.

# Al analizar los valores obtenidos y la matriz de confusión de lso 3 modelos, el algoritmo Logistic Regression es el que mejor resultado tiene, con una exactitud del 0.3 de diferente entre la evaluación del training y test (siendo test menor que el training), esto quiere decir que clasificó correctamente el total de las muestras. Por lo tanto, según la investigación realizada se concluye que si se va a diagnosticar el Cáncer de mama los modelos más indicados para hacerlo son el Logistic Regression  y Decision Trees.

De:
Jacqueline Reina Alvarado
