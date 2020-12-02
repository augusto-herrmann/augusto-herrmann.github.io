---
layout: post
title: "É 2020. Por que você ainda não está abrindo dados? Bingo!"
author: "Augusto Herrmann"
lang: pt
ref: 2020-02-19-its-2020-why-are-you-not-opening-up-data-yet-bingo
category: [pt, blog]
tags: [dados abertos, publicador de dados]
cover: /assets/images/2020/02/sydney-rae-geM5lzDj4Iw-unsplash.jpg
snippet-image: /assets/images/2020/02/italian-open-data-bingo.gif
desc: >-
  Um novo ano chegou e algumas pessoas ainda estão usando velhas desculpas
  para não abrir dados que deveriam estar disponíveis para o público utilizar.
  Como poderíamos abordar essas preocupações e dissuadir algumas objeções que
  as pessoas ainda podem ter?
image-credits: "sydney Rae / Unsplash"
---

Quando eu comecei a defender a ideia e construir dados abertos onze anos
atrás, o mundo era um lugar muito diferente. O Brasil não tinha nem um portal
de dados abertos, nem uma política para isso. Até os países que foram
pioneiros na agenda dos dados abertos estavam apenas começando.

Agora podemos ver uma paisagem muito diferente. A maioria dos países
Now we can see a very different landscape. Most nation states have
[se uniram à agenda dos dados abertos](https://opendatacharter.net/) e
disponibilizam um portal único onde as pessoas podem baixar uma miríade
de dados sobre quase qualquer assunto, incluindo
[os mais importantes](https://index.okfn.org/place/). Muitos governos
locais o fazem, também.

Pode parecer que os gestores do setor público, deste então, em sua maior
parte, foram convencidos das
[motivações](https://opendatahandbook.org/guide/en/why-open-data/)
[para](https://okfn.org/opendata/why-open-data/)
[abrir](https://theodi.org/article/what-is-open-data-and-why-should-we-care/)
[os](https://kit.dados.gov.br/vantagens-dados-abertos/)
[dados](https://www.europeandataportal.eu/en/using-data/benefits-of-open-data),
sejam elas o crescimento econômico, a criação de empregos, a economia de
recursos públicos e eficiência, a melhoria de serviços públicos e privados,
uma forma mais inteligente de abordar os desafios sociais, melhorar a
transparência e responsabilização no setor governamental, ou ainda efeitos
positivos não previstos.

<figure markdown="1">
![Diagrama sobre os benefícios dos dados abertos, do Portal Europeu de Dados]({{ 'assets/images/2020/02/vantagens-dados-abertos.gif' | relative_url }})
<figcaption>Diagrama sobre os benefícios dos dados abertos, do <a href="https://www.europeandataportal.eu/en/using-data/benefits-of-open-data" target="_blank">Portal Europeu de Dados</a>.</figcaption>
</figure>

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2019-11-25-on-the-state-of-open-data-does-it-face-an-identity-crisis" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

Entretanto, como pesquisas como o
[Open Data Index](https://index.okfn.org/place/),
[Open Data Barometer](https://opendatabarometer.org/?_year=2017&indicator=ODB)
e [Open Data Inventory](https://odin.opendatawatch.com/report/rankings) têm
mostrado, ainda há muitas lacunas em dados importantes e potencialmente úteis
que deveriam estar disponíveis, mas não estão. Ainda estamos longe de viver em
uma utopia dos dados abertos. Para mais sobre essa discussão, por favor veja a
minha postagem anterior:
“[{{ reference_post.title }}]({{ reference_post.url | relative_url }})”.

A realidade é que os dados abertos não decolaram de verdade com os políticos.
Raramente um reconhece a existência da agenda, quanto mais defini-la como uma
prioridade política para o desenvolvimento econômico. Isso é a despeito do
fato que, quanto mais dados abertos estiverem disponíveis, mais eles
possibilitam ao setor privado alavancar aplicações emergentes de inteligência
artificial e inovar em produtos e serviços.

Todavia, para pessoas que trabalham no setor público e para pessoas que
frequentemente tentam obter dados a partir de governos usando leis de
acesso à informação, acontece muito dos dados serem negados ou dificultados
por gestores, usando as mesmas velhas desculpas que temos ouvido durante
muitos anos.

## O Bingo dos Dados Abertos

Um conjunto de números que você fica esperando cada um ser anunciado. Bingo!
Essa é a provável inspiração para o nome do
[Open Data Bingo original](http://data.dev8d.org/devbingo/bingo.php?n=1&w=4&h=4&title=%22Open+Data+Excuse%22+Bingo&tag=%23openDataExcuses&statements=Terrorists+will+use+it%0D%0AData+Protection%0D%0ALawyers+want+a+custom+License%0D%0APoor+Quality%0D%0AThieves+will+use+it%0D%0AWe%27ll+get+spam%0D%0AIt%27s+not+very+interesting%0D%0AIt%27s+too+complicated%0D%0AThere%27s+no+API%0D%0AWhat+if+we+want+to+sell+it+later%0D%0AI+don%27t+mind%2C+but+someone+else+might%0D%0AIt%27s+too+big%0D%0AThere%27s+already+a+project+to...%0D%0APeople+may+misinterpret+the+data%0D%0AWe+might+want+to+use+it+in+a+paper%0D%0AWe+will+get+too+many+enquiries&rules=%3Cp%3EFor+open+data+teams%3B+print+out+a+copy+and+put+it+on+your+office+wall.+Cross+out+each+excuse+people+give+you.+There+are+no+prizes%2C+but+you+can+tweet+%22bingo!+%23openDataExcuses%22+if+you+think+it+might+make+you+feel+better*.%3C%2Fp%3E%0D%0A%0D%0A%3Cp+style%3D%27font-size%3A80%25%27%3E*+it+won%27t%3C%2Fp%3E).
É apenas uma tabela das desculpas mais comuns que as pessoas dão para não
abrir os dados. Então, ele foi melhorado por algumas pessoas, entre elas
Christopher Gutteridge (Universidade de Southampton) e Alexander Dutton
(Universidade de Oxford), colaborando em um
[documento do Google Docs](https://docs.google.com/document/d/1nDtHpnIDTY_G32EMJniXaOGBufjHCCk4VC9WGOf7jK4/edit#heading=h.kuxx5ny497m9).
Foi então que o grupo italiano
[Spaghetti Open Data](http://www.spaghettiopendata.org/), e
[Francesco Minazzi](https://twitter.com/digitjus) em particular, adaptaram
o Bingo ao cenário italiano dos dados abertos e produziram um site:
“[Il bingo delle scuse](http://gbonanome.github.io/opendatabingo/about.html)”.

<figure markdown="1">
![O Open Data Bingo italiano]({{ 'assets/images/2020/02/italian-open-data-bingo.gif' | relative_url }})
<figcaption>O Open Data Bingo italiano</figcaption>
</figure>

Algum tempo depois, a ativista dos dados abertos e atual Diretora do
[capítulo da Open Knowledge Foundation no Brasil](https://br.okfn.org/), a
[Fernanda Campagnucci](http://umdadoamais.com/), traduziu e adaptou parte do
conteúdo à realidade brasileira, trazendo da sua experiência em abrir dados na
administração municipal de São Paulo. Ela subiu
[um site](https://campagnucci.github.io/opendatabingo/) com essa versão. Ela,
então, mencionou isso quando foi convidada a um episódio do
[Podcast Pizza de Dados](http://umdadoamais.com/dados-do-ponto-de-vista-do-governo-pizza-de-dados/),
e foi assim que eu ouvi dizer pela primeira vez do open data bingo.

Ao considerar os argumentos na adaptação desse conteúdo para tantos países e
culturas diferentes, é notável o qual semelhantes são entre eles as barreiras
à abertura de dados.

## bingo.dadosabertos.social

Então eu terminei a tradução e adaptação ao contexto brasileiro do resto das
questões que ainda estavam em italiano, e coloquei em um domínio com nome
legal. Assim, surgiu o [bingo.dadosabertos.social](https://bingo.dadosabertos.social/).
Espero que isso ajude a comunidade brasileira de dados abertos a argumentar
com mais eficácia para obter dados das administrações públicas. Vamos tentar,
então, preencher essas lacunas de dados importantes que deveriam, mas ainda
não estão abertos!

Assim como esse projeto não começou comigo, ele não deveria parar por aqui.
Ele usa uma licença completamente aberta e está
[disponível no Github](https://github.com/augusto-herrmann/opendatabingo).
Então faça o seu *fork*, crie a sua versão e me envie um *pull request* se
você tem um argumento útil contra as desculpas para não abrir dados. Se não
tem familiaridade com o Github, deixe os seus comentários no
[fórum dadosabertos.social](https://dadosabertos.social/t/e-2020-por-que-voce-ainda-nao-esta-abrindo-dados-bingo/213).
Se você conhece o contexto das leis brasileiras, instituições e o panorama de
dados, melhor ainda! Suas contribuições serão muito bem vindas.

