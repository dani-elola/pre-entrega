# **ANÁLISIS DEL CATÁLOGO DE NETFLIX**

## Introducción - Objetivo

Dada la expansión y gran variedad de plataformas de streaming con material audiovisual con sus diferentes propuestas de catálogo de contenido, se realiza un análisis con la propuesta de una de las plataformas con mayor cantidad de suscriptores a nivel mundial.

Con el análisis se pretende identificar la clave del éxito que hace que Netflix siga siendo por amplia ventaja la plataforma más elegida por los usuarios.


## Contexto

Netflix cuenta con un catálogo de mas de 8000 títulos que se analizan para responder las siguientes preguntas planteadas y entender si a partir de las respuestas se puede explicar el éxito de la plataforma:

* De qué país predomina el contenido?
* Qué tipo de contenido predomina en el catálogo?
* De qué año hay más contenido? cuál es el año del título más antiguo y cuál el más reciente?
* Quién es el director con más contenido en el catálogo?
* Qué categoría predomina?


## Datos

Los datos para el análisis se toman del dataset "Netflix Movies and TV Shows" disponible en kaggle.com (datasets/netflix_titles.csv).
El dataset está compuesto por 13 columnas y 8807 filas de data, principalmente nombres en formato str y fechas/años en formato int64.
Los labels originales son: show_id |type | title | director | cast | country | date_added | release_year | rating | duration | listed_in | description | Unnamed: 12.


## Metodología

- Se aplica index al dataframe generado a partir del archivo csv para conocer el rango del índice autogenerado.
- Se aplican size y los métodos head() e info() para conocer el tamaño e identificar el contenido y tipos de datos del dataframe.
- Una vez obtenidos los labels, se aplica drop() para eliminar aquellas columnas que no aportan información relevante para el análisis planteado: 'show_id', 'cast', 'rating', 'duration', 'description', 'Unnamed: 12'.
- Con el método describe() se identifica para el label 'release_year' el mínimo y máximo valor.
- Se convierte la fecha del label 'date_added' de str a int64 utilizando la función to_datetime.
- Se renombra el label 'listed_in' por 'category' que es más representativo del contenido de la data.
- Se aplica la función is_unique en la columna 'title' para conocer si cada registro es único.
- Se genera una tabla con la clasificación de la data:

<table><tr><td class="selected" colspan="1" rowspan="1" style="display: table-cell; text-align: left;"><div class="wrap"><div style="margin: 10px 5px;"></div></div></td><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>Data classification</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>type</span></p></div></div></td><td colspan="1" rowspan="1" style="display: table-cell; text-align: left;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>categórico nominal, str</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>title</span></p></div></div></td><td colspan="1" rowspan="1" style="display: table-cell; text-align: left;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>categórico nominal, str</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>director</span></p></div></div></td><td colspan="1" rowspan="1" style="display: table-cell; text-align: left;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>categórico nominal, str</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>country</span></p></div></div></td><td colspan="1" rowspan="1" style="display: table-cell; text-align: left;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>categórico nominal, str</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>date_added</span></p></div></div></td><td colspan="1" rowspan="1" class="selected" style="display: table-cell; text-align: left;"><div class="wrap"><div class="" contenteditable="false" style="margin: 10px 5px;"><p><span>numérico, int</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>release_year</span></p></div></div></td><td colspan="1" rowspan="1" class="selected" style="display: table-cell; text-align: left; vertical-align: top;"><div class="wrap"><div style="margin: 10px 5px;"><p><span>numérico, int</span></p></div></div></td></tr><tr><td colspan="1" rowspan="1" style="display: table-cell; text-align: left; font-weight: bold;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>category</span></p></div></div></td><td colspan="1" rowspan="1" style="display: table-cell; text-align: left;" class="selected"><div class="wrap"><div style="margin: 10px 5px;"><p><span>categórico nominal, str</span></p></div></div></td></tr></table>

- Se aplica el método value_counts() al label 'type' para determinar qué tipo de contenido predomina en el catálogo.
- Se aplica el método value_counts() al label 'release_year' para saber de qué año hay más contenido.
- Se aplican métodos min() y max() al label 'release_year' para identificar de qué año es el titulo más antiguo y de qué año el más reciente.
- Se aplica el método value_counts() a los labels 'director' y 'country' para obtener la información de cuál es el director que predomina en el catálogo y de qué país hay mayor cantidad de contenido.
- Se generan nuevos df auxiliares luego de aplicar el método isnull() a diferentes columnas para obtener cantidad de data y calcular porcentajes.
- Se aplica el método value_counts() a 'category' para visualizar la catogoría predominante. El resultado no es satisfactorio, pues se identifica que existe más de una categoría para cada título. Se pasa la data de la serie 'category' a una estructura de datos de tipo lista para mediante el uso de split separar en str cada categoría, y utilizando el método get poder acceder al primer elemento. Se genera una función lambda para que sustituya toda la lista por el primer elemento sin éxito.


## Resultados

### Para las preguntas planteadas al inicio, luego del análisis de los datos, se obtiene:

* _**De qué país predomina el contenido?**_

    - El contenido de Estados Unidos es el que predomina en el catálogo con 2818 títulos, que representa el 35% de los títulos que tienen identificado el país de origen. 
        Se presenta el Top 5 de países:

|País | Cantidad de titulos |
|---:|---:|
| Estados Unidos | 2818 |
| India | 972 |
| United Kingdom | 419 |
| Japan | 245 |
| South Korea | 199 | 


* _**Qué tipo de contenido predomina en el catálogo?**_

    - Predominan las películas por sobre las series o shows de tv y representan casi el 70% del contenido de la plataforma.
    
|Tipo   |  Cantidad  |
|---:|---:|
|Movie   |  6131  |
|TV Show |  2676  |


* _**De qué año hay más contenido? cuál es el año del titulo más antiguo y cuál el del más reciente?**_

    - Del año 2018 es que se encuentran más títulos en el catálogo con un total de 1147 que representa el 13% de los títulos.
    - El título más antiguo corresponde al año 1925, y el más reciente al año 2021.


* _**Quién es el director con más contenido en el catálogo?**_

    - Esta distribución es muy dispersa, el director con más títulos cargados en el catálogo es Rajiv Chilaka con 19. Se obtienen 4528 datos con nombres de directores diferentes, en 6173 registros de ésta serie, se encuentran además 2634 sin dato (vacíos).


* _**Qué categoría predomina?**_

    - No fue posible responder esta pregunta de manera adecuada. Con el método count_values() sin limpiar la lista de categorías se obtiene que la categoría que predomina en el catálogo es Dramas, International Movies.

        
## Conclusión

Netflix mantiene bastante actualizado su catálogo de contenidos siendo que en el top 5 de años de los títulos encontramos 2018, 2017, 2019, 2020 y 2016, que sumados representan el 57% del contenido. A su vez, tiene una fuerte tendencia hacia las películas, apuntando asi al público cinéfilo. Sus categorías son de lo más variadas pudiendo obtener un universo bien amplio respecto a las edades de suscriptores y/o televidentes.

--> Se podría analizar más en detalle por categoría de contenido pero no fue posible obtener la información.


## Anécdotas 

Para profundizar en la clave del éxito de Netflix se propone analizar cuánto del contenido es generado por la plataforma, y cuántas visualizaciones tiene el contenido propio respecto a las visualizaciones de contenido de todo el catálogo disponible.
