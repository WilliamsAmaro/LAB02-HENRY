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

#### ETL
En el notebook ETL, se observa la importación de dataset Accidentes como dataframe y se empieza a hacer una limpieza.

**1. Objetivo:**
- Visualizar la naturaleza de las variables (categóricas o numéricas).
- Creación de nuevas variables a partir de variables origen del dataset inicial.

**2. Cambios:** Se creó las siguientes variables: Año, Decada, Valor Decada, Hora accidente, Sobrevivientes, Sobrevivientes pasajeros, dummies (Military y Comercial).
- Año: A partir de fecha, se crea esta columna para facilitar el análisis y la visualización posterior.
- Decada: A partir de año los agrupa en décadas, comenzando desde 1901 a 1910 y culminando en 2021-2030.
- Valor Decada: Al ser la variable Decada un String permite darle un valor secuencial u ordinal.
- Hora accidente: A partir de Hora declarada se hace la modificación para poder visualizar o analizar posteriormente.
- Sobrevivientes: A partir de la diferencia de Cantidad de fallecidos respecto a la cantidad registrada de tripulantes (all_aboard)
- SObrevivientes pasajero: Similiar a sobrevivientes, pero restringe solo los sobrevivientes que son pasajeros.
- Dummies (Military y Comercial): A partir de Operador se observó una tendencia (palabra: Military) y se dispuso a generar dummies de aquellos valores que continenen o no la palabra Military.
  
