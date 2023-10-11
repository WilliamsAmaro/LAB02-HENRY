# LAB02-HENRY

#### Contexto
Se plantea la necesidad de analizar datos históricos de accidentes aéreos a los efectos de identificar patrones, tendencias y factores que ayuden a mejorar la seguridad en la aviación civil.
Para ello se presentan los siguientes objetivos:
- KPI: Disminuir un 10% tasa de fatalidad.
- KPI: Aumentar un 10% tasa de supervivencia

Asimismo, a partir de los objetivos propuestos se dispone a relacionar los KPI con otra variables del dataset.

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
  
