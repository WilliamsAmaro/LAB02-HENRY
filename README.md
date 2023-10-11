# LAB02-HENRY

#### **Contexto**
Se plantea la necesidad de analizar datos históricos de accidentes aéreos a los efectos de identificar patrones, tendencias y factores que ayuden a mejorar la seguridad en la aviación civil.
Para ello se presentan los siguientes objetivos:
- KPI: Disminuir un 10% tasa de fatalidad.
- KPI: Aumentar un 10% tasa de supervivencia

Asimismo, a partir de los objetivos propuestos se dispone a relacionar los KPI con otra variables del dataset.

Claro, puedo ayudarte con eso. Aquí está el significado de cada columna en tu conjunto de datos de accidentes aéreos:

- fecha: La fecha en que ocurrió el accidente aéreo.
- hora declarada: La hora declarada del accidente.
- ruta: La ruta del vuelo.
- operador: El operador del vuelo, generalmente la aerolínea.
- flight_no: El número de vuelo.
- route: Otra columna que indica la ruta del vuelo. Podría ser similar a la columna “Ruta”.
- ac_type: El tipo de aeronave involucrada en el accidente.
- registration: El número de registro de la aeronave.
- cn_ln: Probablemente se refiere al número de serie del constructor o al número de línea, que son identificadores únicos para la aeronave.
- all_aboard: El número total de personas a bordo del avión.
- pasajeros a bordo: El número de pasajeros a bordo del avión (excluyendo la tripulación).
- crew_aboard: El número de miembros de la tripulación a bordo del avión.
- cantidad de fallecidos: El número total de muertes en el accidente.
- passenger_fatalities: El número de pasajeros que murieron en el accidente.
- crew_fatalities: El número de miembros de la tripulación que murieron en el accidente.
- ground: El número de personas en tierra que murieron como resultado del accidente.
- summary: Un resumen o descripción del accidente.

#### **ETL**
En el notebook ETL, se observa la importación de dataset Accidentes como dataframe y se empieza a hacer una limpieza.

**1. Objetivo:**
- Visualizar la naturaleza de las variables (categóricas o numéricas).
- Crear nuevas variables a partir de variables origen del dataset inicial.

**2. Cambios:** 
Se creó las siguientes variables: Año, Decada, Valor Decada, Hora accidente, Sobrevivientes, Sobrevivientes pasajeros, dummies (Military y Comercial).
- Año: A partir de fecha, se crea esta columna para facilitar el análisis y la visualización posterior.
- Decada: A partir de año los agrupa en décadas, comenzando desde 1901 a 1910 y culminando en 2021-2030.
- Valor Decada: Al ser la variable Decada un String permite darle un valor secuencial u ordinal.
- Hora accidente: A partir de Hora declarada se hace la modificación para poder visualizar o analizar posteriormente.
- Sobrevivientes: A partir de la diferencia de Cantidad de fallecidos respecto a la cantidad registrada de tripulantes (all_aboard)
- Sobrevivientes pasajero: Similiar a sobrevivientes, pero restringe solo los sobrevivientes que son pasajeros.
- Dummies (Military y Comercial): A partir de Operador se observó una tendencia (palabra: Military) y se dispuso a generar dummies de aquellos valores que continenen o no la palabra Military.

  #### **EDA**
  En el notebook EDA, se observa el análisis exploratorio de las variables del dataset, a modo de obtener insights.

  **1. Objetivo**
  - Vizualizar el tipo y comportamiento de las variables y entre variables (incluyendo frecuencia).
  - Crear un csv con los cambios efectuados.
  
  **2. Trabajo**
  
  Con describe:
- _Tamaño del Conjunto de Datos: El conjunto de datos consta de 5008 observaciones. Sin embargo, algunas columnas tienen valores faltantes, como "PASAJEROS A BORDO" y "crew aboard," lo que indica que no todas las observaciones tienen información completa en esas columnas._
- _Variables Dummy (Military y Comercial): Las variables dummy "Military" y "Comercial" indican si un accidente está asociado con vuelos militares o comerciales. Los valores promedio muestran que la mayoría de los accidentes en el conjunto de datos están relacionados con vuelos comerciales en lugar de vuelos militares._
- _En promedio, hay alrededor de 31 personas a bordo de una aeronave, con un valor medio de 4.52 tripulantes a bordo. La cantidad promedio de fallecidos es de aproximadamente 22.29, con 18.94 fallecidos entre los pasajeros y 3.59 entre la tripulación._

  Correlación:
![Imagen](https://github.com/WilliamsAmaro/LAB02-HENRY/blob/main/Correlaci%C3%B3n.png)
  _La matriz de correlación muestra la relación entre las diferentes variables en nuestro conjunto de datos._
- _Correlación Negativa entre Tripulantes Fallecidos y Vuelos Comerciales (-0.274762): Hay una correlación negativa entre la cantidad de tripulantes fallecidos y la categoría de vuelos comerciales. Esto podría indicar que los accidentes con tripulantes fallecidos tienden a estar menos relacionados con vuelos comerciales y podrían estar más asociados con operaciones militares u otros tipos de vuelos._
- _Correlación Perfectamente Negativa entre Categorías Militares y Comerciales (-1.0): La matriz muestra una correlación perfectamente negativa entre las categorías de vuelos militares y comerciales, lo que significa que las observaciones se dividen claramente en dos categorías mutuamente excluyentes. Esto es importante para distinguir entre vuelos militares y comerciales en el análisis._
- _Hora del Accidente con Correlación Muy Débil (0.015154): La hora del accidente tiene una correlación muy débil con las categorías de vuelos militares y comerciales. Esto indica que la hora del accidente no está fuertemente relacionada con el tipo de operación y, por lo tanto, es menos relevante en ese contexto._

  __Frecuencias:__

  ___Número de accidentes por año___
  ![Imagen](https://github.com/WilliamsAmaro/LAB02-HENRY/blob/main/AccidentesA%C3%B1o.png)
  _Nota: Se puede observar que la cantidad de accidentes alcanzan una frecuencia mayor en la década de 1940-1950, periodo que coincide con la 2da guerra mundial, asimismo, esta frecuencia se mantiene casi constante lo cual coincidiría con el periodo de la guerra fría._

  ___Relación accidentes Militares y Comerciales___
  ![imagen](https://github.com/WilliamsAmaro/LAB02-HENRY/blob/main/RelacionMyC.png)
  _Nota: En el gráfico se observa la distribución de accidentes aéreos por su origen durante el período de 1908 a 2021. Los datos revelan que los accidentes de origen militar constituyen el 15.2% del total, mientras que los accidentes de origen comercial representan el 84.8%. Esto sugiere que la aviación comercial es un sector de alta actividad y que las aerolíneas comerciales enfrentan una mayor cantidad de incidentes en comparación con su contraparte militar; sin dejando de lado que la proporción de accidentes de origen militar fueron ocasionados por la guerra o entrenamientos militares (siendo el siglo XX una época muy belicosa). En conlusión, se ha visto como la industría de la aerolínea comercial ha avasallado a los accidentes de origen militar, por lo que se subraya la necesidad constante de mejorar la seguridad en la aviación comercial. Estos insights son esenciales para garantizar que la seguridad siga siendo una prioridad en la industria de la aviación._

  ___Summary (registro del accidente)___
  ![imagen](https://github.com/WilliamsAmaro/LAB02-HENRY/blob/main/Summary.png)
  _Nota: El gráfico proporciona pistas valiosas sobre las causas predominantes de los accidentes aéreos. Al analizar los términos más frecuentemente asociados con los accidentes, como "crashed," "aircraft," "plane," "crew," "flight," "pilot," "runway," "engine," "approach," y "failure," podemos extrapolar y comprender mejor las posibles causas subyacentes._
- _Accidentes de Vuelo: La alta frecuencia de términos como "flight," "pilot," "aircraft," y "plane" sugiere que los problemas relacionados con la operación de aeronaves y - la labor de los pilotos son causas frecuentes de accidentes._
- _Fallas Técnicas: La presencia de "engine" y "failure" indica que problemas técnicos, posiblemente relacionados con fallas en los motores o sistemas de la aeronave, pueden contribuir a los accidentes._
- _Factores Humanos: Los términos "crew" y "runway" sugieren que factores humanos, incluyendo errores de la tripulación y problemas en el despegue o aterrizaje, también pueden desempeñar un papel importante._
- _Problemas en la Aproximación: La inclusión de "approach" señala que los problemas en la fase de aproximación al aterrizaje pueden ser una causa común de accidentes._
- _Tipo de Aeronave: Los términos "aircraft" y "plane" sugieren que el tipo de aeronave utilizada puede influir en la probabilidad de accidentes._

  ___Tasa de Fatalidad por década___
  ![imagen](https://github.com/WilliamsAmaro/LAB02-HENRY/blob/main/KPI_1.png)
  _Nota: El gráfico de barras ilustra la evolución del ratio de crew fatalities en accidentes aéreos a lo largo de diferentes décadas desde 1901 hasta la actualidad. Se observa un patrón interesante: el ratio comenzó en 0 durante la década de 1901-1910, lo que podría indicar un inicio relativamente seguro de la aviación. Sin embargo, a medida que avanzamos en el tiempo, el ratio aumentó constantemente hasta la década de 1970, alcanzando su punto máximo. A partir de entonces, se estabilizó, pero en un nivel significativamente superior al inicio. Este análisis subraya la importancia continua de mejorar la seguridad en la industria de la aviación, a pesar de los avances tecnológicos y las regulaciones de seguridad implementadas._

  ___Ingesta de la data Aa MySQL___
  ![imagen](https://github.com/WilliamsAmaro/LAB02-HENRY/blob/main/CAPTURAMYSQL.png)

### **DASHBOARD E INSIGTHS**
