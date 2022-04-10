# **ANALISIS DEL CATÁLOGO DE NETFLIX**

## Introducción - Objetivo

Dada la expansión y gran variedad de plataformas de streaming con material audiovisual, con sus diferentes propuestas de catálogo de contenido, se entiende necesario realizar un análisis con la propuesta de una de las plataformas con mayor cantidad de suscriptores a nivel mundial.

Con el análisis se pretende identificar la clave del éxito que hace que Netflix siga siendo por amplia ventaja la plataforma más elegida por los usuarios.


## Contexto

Netflix cuenta con un catálogo de mas de 8000 títulos que se analizan para responder las siguiente preguntas planteadas y entender si a partir de las respuestas se puede explicar el éxito de la plataforma:

* De qué país predomina el contenido?
* Qué tipo de contenido predomina en el catálogo?
* Qué año tiene mas contenido y de que año es el contenido más antiguo y más reciente?
* Cuál es el director con más contenido en el catálogo?
* Qué categoría predomina?


## Datos

Los datos para el análisis se toman del dataset "Netflix Movies and TV Shows" disponible en kaggle.com (datasets/netflix_titles.csv).
El data set está compuesto por 13 columnas y 8806 filas de data, principalmente nombres en formato str y fechas/años en formato int.
Los labels originales son: 	show_id	type | title | director	cast | country | date_added	| release_year | rating | duration | listed_in | description | Unnamed: 12
