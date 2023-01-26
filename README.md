# <h1> **PROYECTO INDIVIDUAL Nº2** </h1>


<br>

¡Hola! Soy *Yamila Galiano* y este es mi segundo proyecto del bootcamp de Data Science en SoyHenry, enfocado en Machine Lerning.

<hr>  

### Objetivo
A partir de datasets, generar un modelo de predicción de datos usando métricas para medir la performance de los mismos. 
##
[Consigna completa del LAB - Cohorte 6](https://github.com/YamiGaliano/LAB02-Datathon/blob/main/Consigna-Henry.md)


### Contexto
Como parte del área de Machine Lerning de una empresa del rubro de la inmobiliaria en Estados Unidos, el Team Lider le propone dos predicciones posibles, de las cuales puede elegir cuál realizar (o ambas si así lo quiere): ​

- Implementar un modelo de clasificación con aprendizaje supervisado que permita clasificar el precio de las propiedades en venta, utilizando los datos que se han puesto a su disposición. ​ Para esto debe crear la columna category_price, en la cual se consideran las categorías
    - 'low': Para precios entre 0 y 999 dólares.
    - 'high': Para precios desde 1000 en adelante. ​ Considerando esta categorización, el objetivo es predecir si una propiedad pertenece a la categoría de precios bajos (low). ​
- Implementar un modelo de clasificación con aprendizaje no supervisado, utilizando clustering que agrupe las propiedades por segun las 3 categorias a las que pueden pertenecer.​


### Tecnologías utilizadas
* [Python](https://docs.python.org/3/)
* [Pandas](https://pandas.pydata.org/)
* Seaborn y Matplotlib 
* Numpy
* Sklearn


<hr>
<br/>
 <br>

## Archivos del repositorio
- [**Datasets**:](./Datasets/) En esta carpeta se encuentran los archivos .csv utilizados para realizar el proyecto y también el archivo que se creó con los resultados de las predicciones.
- [**Archivos parquet**:](https://drive.google.com/drive/folders/1nJ9ZMj6E6zh6McC9NwCA6KopfUIOG_1O) Aquí se encuentran los archivos provistos para realizar los modelos.
- [**EDA.ipynb**:](EDA.ipynb) Notebook con el desarrollo del EDA en los datasets.
- [**modelo_ns.ipynb**:](modelo_ns.ipynb) Notebook con modelo no supervisado desarrollado.
- [**modelo_s1.ipynb**:](modelo_s1.ipynb) Notebook con modelo supervisado con datasets con nulos eliminados.
- [**modelo_s2.ipynb**:](modelo_s2.ipynb) Notebook con modelo supervisado con datasets con nulos remplazados. 

<br/>

## Tareas realizadas
### EDA
Importamos y damos un primer vistaso a los datasets para validar tipos de datos y cantidad de nulos. </p>
Quitamos duplicados en image_url & description de publicaciones generados varias veces manteniendo el último registro con el precio mayor (keep='last'). </p>
Creamos variable objetivo solicitada 'category_price' donde el precio low (0-999) es 0 y el precio high (1000 en adelante) es 1. </p>
Analizamos el mapa, para validar si la lat y long se encuentran ok o tenemos outliers. Analizamos si corresponden a los límites de EEUU con un poligono. El mismo tiene un margen de error para las ciudades limitrofes. Descargamos el geo mapa de https://exploratory.io/map. Luego de descartar varias ciudades que si concuerdan con el pais de EEUU, validamos con un listado de .cvs descargados de la siguiente [página](https://catalog.data.gov/dataset/?q=list+of+cities&sort=views_recent+desc&ext_location=&ext_bbox=&ext_prev_extent=-150.46875%2C-80.17871349622823%2C151.875%2C80.17871349622823).</p>
Detectamos Outliers de las variable 'price', 'sqfeet', 'beds'. Procedemos a eliminarlos y eliminar las columnas generadas que no aportan al dataset(['geometry', 'in_usa', 'valid_region','zscore','url', 'region_url','image_url','description']). </p>
Realizamos un analisis de correlación con todos los datos numericos. </p>
Revisamos nuevamente nulos y separamos dataframes. Uno de ellos tiene los datos nulos de 'laundry_options' y 'parking_options' remplazados por 'Unknown': properties_train_rep.csv. El otro tiene los datos nulos de 'laundry_options' y 'parking_options' eliminados: properties_train_wn.csv. Los datos nulos de 'lat' y 'long' fueron eliminados en ambos archivos. </p> 

### Modelos supervisados
- [Modelo_s1](modelo_s1.ipynb). En este archivo se generaron varios modelos supervisados con el dataset  properties_train_wn.csv que tiene los datos nulos eliminados. 
    - Modelo 1. En este modelo se comenzo con un árbol de desición donde se contemplaron las columnas cuantitativas solamente que se detallan en la Notebook. Obtuvimos un score de 0.66 para el set de train. En el Datathon obtuvimos un Acurrency de 0.74. 
    - Modelo 1.2. En este modelo se realizo un árbol también pero donde se cambiaron las variables cualitativas: 'laundry_options', 'parking_options' y 'state' a variables cuantitativas con el módulo map. Obtuvimos un score de 0.73. 
    - Modelo 1.3. En este modelo de árbol, se realizo una reducción de columnas a contemplar. Se seleccionaron las 3 que más relevancia tenian respecto al precio del inmueble. Obtuvimos un score de 0.67. 
    - Modelo 1.4. En este modelo se utilizo vecinos y se seleccionaron todas las variables más relevantes. Obtuvimos un score de 0.87.


- [Modelo_s2](modelo_s2.ipynb). En este archivo se genero un modelo supervisado con el archivo properties_train_rep.csv que tiene los datos nulos remplazados. 
    - Modelo 2. En este modelo se utilizo un árbol de desición donde solo se contemplaron las columnas cuantitativas. Obtuvimos un score de 0.64. 

- [Modelo_nosupervisado](modelo_ns.ipynb). En este archivo se genero un modelo no supervisadocon el archivo properties_train_wn.csv que tiene los datos nulos eliminados. 
    - Modelo 3. En este modelo se utilizo Kmeans para realizar las predicciones con 3 clusters. Se generaron variables cuantitativas de 'laundry_options', 'parking_options' y 'state' a variables cuantitativas con el módulo map. Obtuvimos un score de 0.72. Al subirlo al Datathon obtuvimos un score de 0.015. 
<hr>
<br/>

Contacto:  </p> <a href="https://www.linkedin.com/in/yamila-galiano-ba7083121"><img alt="Linkedin" src="https://img.shields.io/badge/Linkedin-0077B5?style=flat&logo=linkedin&logoColor=white"></a>  
