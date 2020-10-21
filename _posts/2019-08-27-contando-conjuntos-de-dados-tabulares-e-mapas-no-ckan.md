---
layout: post
title: "Contando conjuntos de dados tabulares e mapas no CKAN"
author: "Augusto Herrmann"
lang: pt
ref: 2019-08-27-counting-tabular-and-map-datasets-in-ckan
category: [pt, blog]
tags: [dados abertos, ckan, jupyter notebook, tutorial]
cover: /assets/images/2019/08/fleur-dQf7RZhMOJU-unsplash.jpg
desc: >-
  Como contar conjuntos de dados tabulares e mapas em uma instância do CKAN
  usando a API, explicado em um caderno Jupyter.
image-credits: "Fleur / Unsplash"
---

Veio ao meio conhecimento que alguns sistemas de avaliação internacionais,
especiifcamente o
[Open-Useful-Reusable Government Data (OURdata) Index](http://www.oecd.org/gov/digital-government/open-government-data.htm),
medido pela Organização para a Cooperação e Desenvolvimento Econômico (OCDE),
medem não apenas quantos conjuntos de dados um dado portal nacional de dados
abertos tem, mas também quantos destes são tabulares e quantos são mapas.


Não creio que medir o número de conjuntos de dados em um portal de dados
abertos governamentais seja uma métrica muito útil, considerando que governos
podem muito bem dividir grandes conjuntos de dados em outros menores para
obter um maior "número de conjuntos de dados", sem acrescentar qualquer
benefício ou valor para o utilizador dos dados.

Pelo contrário, essa prática pode fazer com que dados relevantes se tornem
mais difíceis de encontrar, já que estarão mais espalhados no meio do oceano
de outros conjuntos de dados que podem não ser relevantes no contexto que o
utilizador está procurando.

Opiniões similares sobre o número de conjuntos de dados enquanto métrica são
compartilhadas por organizações da sociedade civil e também governos, como
pode ser visto em postagens de blog da
[Sunlight Foundation](https://sunlightfoundation.com/2019/08/13/measuring-the-impact-of-community-engagement-around-open-data/)
e do [DataSF](https://datasf.org/blog/how-to-measure-open-data/),
o portal de dados abertos da cidade de São Francisco (em tradução livre):


> * **Isso incentiva o comportamento errado.** Se publicarmos cada ano como
>   um conjunto de dados diferente, nosso N sobe, mas a usabilidade dos dados
>   cai. Se publicarmos dados de baixo valor, nosso N sobe, mas ninguém quer
>   usá-los. Embora seja importante rastrear – # de conjuntos de dados não
>   deveria ser um indicador chave de desempenho (KPI).
> * **Isso desvia o foco da qualidade.** Publicar para aumentar o seu N
>   distrai de garantir a publicação de alta qualidade – dados que são
>   documentados, atualizados regularmente e que têm valor.

De fato, outros *rankings* internacionais bem estabelecidos, o
*[Open Data Index](https://index.okfn.org/)*,
o *[Open Data Barometer](https://opendatabarometer.org/)* e o
*[Open Data Inventory](http://odin.opendatawatch.com/)* não medem a quantidade
de conjuntos de dados.


## O que é um conjunto de dados?


De acordo com a recomendação do W3C para Boas Práticas de Dados na Web, um
[conjunto de dados](https://www.w3.org/TR/dwbp/#dataset) é (em tradução livre):

> definido como uma coleção de dados, publicados ou curados por um único
> agente, e disponível para acesso ou download em um ou mais formatos. Um
> conjunto de dados não precisa estar disponível como um arquivo
> descarregável.


[CKAN](https://ckan.org/), o software para catálogos de dados abertos mais
frequentemente usado no mundo, também opera com a noção de um
[conjunto de dados](https://docs.ckan.org/en/2.8/user-guide.html#datasets-and-resources).
Ele segue dividindo conjuntos de dados em recursos, que podem seguir diversos
critérios possíveis, tais como fatias temporais, tabelas inter-relacionadas,
divisões regionais ou departamentais, etc. Recursos também podem ser
disponibilizados em muitos formatos diferentes.

Da documentação do CKAN (em tradução livre):

> Um conjunto de dados é um lote de dados - por exemplo, poderia ser as
> estatísticas criminais para uma região, os valores dos gastos de um
> departamento governamental ou as leituras de temperatura de várias estações
> climáticas. Quando os usuários pesquisam por dados, os resultados que eles
> verão serão conjuntos de dados individuais.
> 
> Um conjunto de dados contém duas coisas:
> 
> * Informação ou “metadados” sobre os dados. Por exemplo, o título e
>   publicador, data, em que formatos está disponível, sob qual licença eles
>   estão disponibilizados, etc.
> * Um número de “recursos”, que guardam os dados em si. O CKAN não se importa
>   com o formato no qual o dados está. Um recurso pode ser uma planilha CSV
>   ou Excel, arquivo XML, documento PDF, arquivo de imagem, linked data no
>   formato RDF, etc. O CKAN pode armazenar o recurso internamente ou
>   guardá-lo simplesmente como um link, estando o recurso em si em outro
>   lugar da web. Um conjunto de dados pode conter qualquer número de
>   recursos. Por exemplo, diferentes recursos podem conter os dados para
>   diferentes anos ou eles podem conter os mesmos dados em diferentes
>   formatos.



Disso concluímos que conjuntos de dados podem conter dados tabulares, mapas,
ambos ou nenhum desses.


Contar quantos conjuntos de dados tabulares e mapas há em uma dada instância
do CKAN oferece alguns desafios:

* eles não são conjuntos disjuntos, i.e., podem existir conjuntos de dados que
  possuam recursos tabulares e mapas no mesmo conjunto de dados
* há múltiplos formatos de dados tabulares e mapas que precisam todos serem
  levados em consideração
* o metadado *formato* nos recursos é um campo de texto livre, frequentemente
  permitindo uma variedade de maneiras de se escrever o mesmo formato (e.g.
  "geoJSON", "geo-JSON", "Geo JSON", etc.)
* a interface de pesquisa por conjuntos de dados permite ao usuário filtrar os
  conjuntos de dados, ou por um formado de cada vez, ou por uma combinação de
  condições de formato que precisam todas elas serem satisfeitas
  simultaneamente, i.e., é uma operação "e" e não "ou". Não se pode pegar
  todas as variantes de formatos simplesmente selecionando cada um dos valores
  de formato que seriam dados de mapas. Por exemplo, selecionar "KML" e
  "GeoJSON" trará apenas conjuntos de dados que têm recursos em KML **e**
  recursos em GeoJSON. Se apenas um destes estiver disponível, o conjunto de
  dados não será incluído.


## Abordagem


Para superar esses desafios, uma solução possível seria usar a API do CKAN
para somar os conjuntos de dados de acordo com critérios especificados, que
definiremos como condições para que formatos sejam aceitos como tabulares e/ou
mapas.


Para isso, faremos uma lista de todos os formatos reconhecidos como tabulares
e outra com todos os formatos considerados como mapas. Considerando que esses
conjuntos não são disjuntos, também precisaremos contar quantos conjuntos de
dados estão em um dos conjuntos mas não no outro, assim como conjuntos de
dados que estão em ambos os conjuntos.


Para este exemplo, utilizaremos o Portal Brasileiro de Dados Abertos,
disponível em dados.gov.br.

```python
CKAN_URL = "http://dados.gov.br"
UA = "ckan-tabular-and-map-counter/1.0 (+https://github.com/augusto-herrmann/ckan-tabular-and-map-counter)"
```

```python
from ckanapi import RemoteCKAN
```

```python
catalog = RemoteCKAN(CKAN_URL, UA)
```

```python
dataset_ids = catalog.action.package_list()
```

O seguinte código fará uma requisição por conjunto de dados para a instância
do CKAN. Isso pode demorar bastante, a depender do número de conjuntos de
dados presente. Certifique-se de ajustar o intervalo entre as requisições
para não sobrecarregar o servidor.

```python
# Temporizar nossos intervalos entre requisições
import time
import random
```

```python
# Intervalo mínimo e máximo, em milissegundos
MIN_DELAY = 100
MAX_DELAY = 5000
```

```python
# Vamos rastrear nosso progresso
from tqdm import tqdm_notebook as tqdm
```

```python
formats = {}
```

Isso deve demorar bastante para rodar.

```python
for dataset_id in tqdm(dataset_ids):
    time.sleep(random.uniform(MIN_DELAY, MAX_DELAY)/1000)
    dataset = catalog.action.package_show(id=dataset_id)
    if dataset['state'] == 'active' and not dataset['private']:
        formats[dataset_id] = [
            resource['format'].lower() 
            for resource in dataset['resources']
        ]
```

Para contar os conjuntos de dados, precisamos primeiro determinar que formatos
serão considerados tabulares e quais são mapas. Para evitar redundâncias,
trataremos todos os formatos em caixa baixa.

Poderíamos usar o metadado do
[MIME Type](https://en.wikipedia.org/wiki/Media_type),
mas descobrimos que na prática esse campo é frequentemente deixado em branco
pelas pessoas que o preenchem.

```python
TABULAR_FORMATS = [
    'csv',
    'xlsx',
    'ods',
    'xls',
    'zip+csv',
    'txt',
    'zip+xls',
    'zip+sas',
    'csv+zip',
    'zip+rar+csv',
    'zip+txt',
]
```

```python
MAP_FORMATS = [
    'kml',
    'geojson',
    'zip shp',
    'esri rest',
    'ogc wms',
    'shp-zip',
    'wms',
    'kmz',
]
```

## Contando conjuntos de dados


Agora vamos contar os conjuntos de dados em cada um desses grupos.


Os seguintes são conjuntos de dados que incluem pelo menos um recurso em um
formato que é considerado tabular.

```python
tabular_datasets = [
    dataset_id
    for dataset_id in dataset_ids
    if set(formats[dataset_id]).intersection(set(TABULAR_FORMATS))
]
```

```python
len(tabular_datasets)
```

Os seguintes são conjuntos de dados que incluem pelo menos um recurso em um
formato que é considerado como mapa.

```python
map_datasets = [
    dataset_id
    for dataset_id in dataset_ids
    if set(formats[dataset_id]).intersection(set(MAP_FORMATS))
]
```

```python
len(map_datasets)
```

Agora contamos conjuntos de dados que têm recursos tabulares, mas não têm
quaisquer recursos de mapas.

```python
tabular_but_not_map_datasets = [
    dataset_id
    for dataset_id in dataset_ids
    if set(formats[dataset_id]).intersection(set(TABULAR_FORMATS))
    and not set(formats[dataset_id]).intersection(set(MAP_FORMATS))
]
```

```python
len(tabular_but_not_map_datasets)
```

E vice versa, conjuntos de dados que têm recursos de mapas, mas nenhum que
seja tabular.

```python
map_but_not_tabular_datasets = [
    dataset_id
    for dataset_id in dataset_ids
    if set(formats[dataset_id]).intersection(set(MAP_FORMATS))
    and not set(formats[dataset_id]).intersection(set(TABULAR_FORMATS))
]
```

```python
len(map_but_not_tabular_datasets)
```

Finalmente, esses são os conjuntos de dados que contêm tanto recursos
tabulares, quanto mapas.

```python
tabular_and_map_datasets = [
    dataset_id
    for dataset_id in dataset_ids
    if set(formats[dataset_id])\
        .intersection(set(TABULAR_FORMATS))\
        .intersection(set(MAP_FORMATS))
]
```

```python
len(tabular_and_map_datasets)
```

## Conclusão


Não obstante a utilidade da métrica, é de fato possível contar os conjuntos de
dados tabulares e mapas no CKAN. Apesar de não ser uma métrica prontamente
disponível, ela pode ser contada com relativa facilidade (apesar de um pouco
lentamente se você tiver muitos conjuntos de dados), usando a API do CKAN.

Este caderno também está disponível
[no Github](https://github.com/augusto-herrmann/ckan-tabular-and-map-counter).

