# 🏋🏻 Análisis de Retención de Clientes para Model Fitness 🏋🏻‍♀️
## Descripción del proyecto
En este proyecto, trabajé con Model Fitness, una cadena de gimnasios que enfrenta el desafío común de la pérdida de clientes. Consciente de la importancia de la retención, la empresa decidió implementar una estrategia basada en datos analíticos para mejorar la interacción con sus usuarios. La retención de clientes se convirtió en una prioridad, ya que identificar cuándo un cliente está a punto de abandonar el servicio no siempre es sencillo. En el caso de los gimnasios, las ausencias prolongadas de los usuarios son un claro indicativo de posible cancelación.
Model Fitness optó por digitalizar los perfiles de sus clientes con el fin de identificar patrones de comportamiento y desarrollar estrategias efectivas que fomenten la lealtad y reduzcan la tasa de cancelación. Mi tarea consistió en analizar los datos disponibles para identificar oportunidades y soluciones que permitieran mejorar la retención de los usuarios, proporcionando recomendaciones basadas en patrones de comportamiento que podrían ayudar a anticipar la pérdida de clientes y ofrecer acciones correctivas oportunas.

## Motivación 
Este proyecto es importante porque permite a Model Fitness desarrollar soluciones personalizadas que fomenten la lealtad de los usuarios. Al analizar los datos, se pueden identificar señales de advertencia, como ausencias prolongadas, y tomar acciones correctivas de manera oportuna. Esto no solo mejora la retención, sino que también optimiza la experiencia del usuario, maximizando el valor de cada cliente. Al centrarse en la retención a través de un enfoque basado en datos, la empresa puede reducir la tasa de cancelación y crear una base de clientes más sólida y fiel.

## Características del Dataset

El dataset incluye los siguientes campos:

##### 'Churn' — la cancelación para el mes en cuestión
- Campos de dataset actuales: Datos del usuario del mes anterior
  
'gender'.

-'Near_Location' — si el/la usuario/a vive o trabaja en el vecindario donde se encuentra el gimnasio.

-'Partner' — si el/la usuario/a trabaja en una compañía asociada (el gimnasio tiene empresas asociadas cuyos empleados obtienen descuentos; en esos casos el gimnasio almacena información sobre los empleadores de los clientes).

-Promo_friends — si el/la usuario/a originalmente se inscribió mediante una oferta “trae a un/a amigo/a” (se utilizó el código promocional de un/a amigo/a cuando pagaron el primer abono).

-'Phone' — si el/la usuario/a aportó el número de teléfono.

-'Age'.

.'Lifetime' — el tiempo (en meses) desde que el/la usuario/a llegó por primera vez al gimnasio.

#### Datos del registro de visitas y compras y datos sobre el estado actual de la membresía:

-'Contract_period' — 1 mes, 3 meses, 6 meses o 1 año.

-'Month_to_end_contract' — los meses que faltan hasta que expire el contrato.

-'Group_visits' — si el/la usuario/a participa en sesiones grupales.

-'Avg_class_frequency_total' — frecuencia media de visitas por semana a lo largo de la vida del cliente.

-'Avg_class_frequency_current_month' — frecuencia media de visitas por semana durante el mes en curso.

-'Avg_additional_charges_total' — cantidad total de dinero gastado en otros servicios del gimnasio: cafetería, productos deportivos, cosméticos, masajes, etc.

## Herramientas Utilizadas
### Lenguaje: 
Python 
### Librerías:
pandas para la manipulación de datos.
numpy para cálculos numéricos.
matplotlib y seaborn para visualizaciones.
scikit-learn para la creación y evaluación de modelos de Machine Learning.
sklearn.tree import DecisionTreeClassifier
sklearn.metrics 
sklearn.preprocessing import StandardScaler
sklearn.model_selection import train_test_split
sklearn.linear_model - LogisticRegression
sklearn.linear_model - Lasso, Ridge
sklearn.tree import DecisionTreeRegressor
sklearn.ensemble 
scipy.cluster.hierarchy as sch
Jupyter Notebook para la documentación del análisis.

## Proceso del Proyecto
### Paso 1: Análisis exploratorio de datos (EDA)

#### Observación del dataset:
Observé el dataset y verifiqué si contenía características ausentes. Utilicé el método describe() para estudiar los valores promedio y la desviación estándar de las variables numéricas. Esto me permitió comprender la distribución de los datos y detectar cualquier anomalía o valores atípicos.

#### Estudio de los valores medios por grupo:
Estudié los valores medios de las características en dos grupos: aquellos usuarios que se fueron (cancelación) y los que se quedaron. Utilicé el método groupby() para segmentar los datos por el estado de cancelación y comparé las características promedio entre ambos grupos.

#### Análisis gráfico:
Trazo histogramas de barras y distribuciones de características para visualizar las diferencias entre los usuarios que se fueron y los que se quedaron. Esto me permitió identificar patrones o diferencias significativas en el comportamiento de los dos grupos.

#### Matriz de correlación:
Creé una matriz de correlación entre las variables para estudiar las relaciones entre las características. Esto me ayudó a identificar qué variables podían estar más estrechamente relacionadas con la cancelación.

### Paso 2: Construcción de un modelo para predecir la cancelación de usuarios

#### Creación del modelo:
Construí un modelo de clasificación binaria para predecir la cancelación de los usuarios el mes siguiente, utilizando la cancelación como la característica objetivo. El objetivo fue identificar qué factores influían en la decisión de cancelación.

#### División de datos:
Dividí los datos en conjuntos de entrenamiento y validación utilizando la función train_test_split(). Esto me permitió entrenar el modelo en un subconjunto de los datos y evaluar su desempeño en otro conjunto separado.

#### Entrenamiento de los modelos:
Entrené dos modelos de clasificación: regresión logística y bosque aleatorio, utilizando el conjunto de entrenamiento. Ambos modelos se ajustaron para predecir la cancelación de usuarios.

#### Evaluación del modelo:
Evalué ambos modelos utilizando métricas de desempeño como la exactitud, precisión y recall sobre el conjunto de validación. Comparé los resultados para determinar cuál modelo tuvo un mejor rendimiento.

### Paso 3: Creación de clústeres de usuarios/as

#### Preprocesamiento de datos:
Dejé de lado la columna de cancelación y estandaricé las características del dataset para asegurarme de que todas las variables estuvieran en la misma escala.

#### Análisis de clústeres:
Utilicé la función linkage() para crear una matriz de distancias basada en las características estandarizadas y tracé un dendrograma. Esto me permitió visualizar las relaciones entre los usuarios y estimar el número óptimo de clústeres.

#### Entrenamiento del modelo de clustering:
Entrené un modelo de clustering con el algoritmo K-means, estableciendo el número de clústeres en 5 para simplificar la comparación. Predije a qué clúster pertenecía cada usuario.

#### Análisis de los clústeres:
Analicé los valores medios de las características para cada clúster, buscando patrones que pudieran diferenciar a los grupos. Luego tracé distribuciones de características para visualizar mejor las diferencias entre los clústeres.

#### Tasa de cancelación por clúster:
Calculé la tasa de cancelación para cada clúster utilizando el método groupby(). Esto me permitió observar si existían diferencias en la tasa de cancelación entre los clústeres y, de ser así, identificar cuáles eran más propensos a la cancelación.

### Paso 4: Conclusiones y recomendaciones

#### Conclusiones:
Llegué a conclusiones sobre los factores clave que influían en la cancelación de los usuarios, basándome en los resultados del análisis de clústeres y los modelos predictivos. Identifiqué patrones de comportamiento que permitieron anticipar la cancelación.





