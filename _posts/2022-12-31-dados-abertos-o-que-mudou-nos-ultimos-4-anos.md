---
layout: post
title: "Dados abertos: o que mudou nos últimos 4 anos"
author: Augusto Herrmann
lang: pt
ref: 2022-12-31-open-data-what-has-changed-in-the-past-4-years
category: [pt, blog]
tags: [dados abertos, cgu, políticas públicas, governo aberto]
cover: /assets/images/2022/12/sander-sammy-53bht9urH1A-unsplash.jpg
snippet-image: /assets/images/2022/12/sander-sammy-53bht9urH1A-unsplash.jpg
desc: >-
  Passados 4 anos desde que a Controladoria-Geral da União recebeu a
  responsabilidade pela política de dados abertos do governo federal, é
  chegada a hora de avaliar o que mudou. O balanço, contudo, é de poucos
  avanços e vários retrocessos.
image-credits: Sander Sammy / Unsplash
---

Passados 4 anos desde que [a Controladoria-Geral da União recebeu a
responsabilidade pela política de dados abertos do governo federal](https://dadosabertos.social/t/cgu-assume-a-politica-de-dados-abertos-do-governo-federal/74),
é chegada a hora de avaliar o que mudou nesse período.

## Como era no início: 2010 a 2015

Antes, contudo, convém lembrar um pouco sobre como a política de dados
abertos era conduzida até então.

Tomei posse em um cargo público no então Ministério do Planejamento em 2010,
ainda isso fosse que financeiramente desvantajoso para mim, apenas pelo meu
interesse pela temática de dados abertos e o desejo de construir como política
pública algo que já despontava nos
[Estados Unidos](https://en.wikipedia.org/wiki/Data.gov) e
[Reino Unido](https://en.wikipedia.org/wiki/Data.gov.uk), que inauguraram
os seus portais de dados abertos em 2009. Eu já estava, desde antes, envolvido
como voluntário em diversos projetos de dados abertos da Open Knowledge
Foundation, tais como o [CKAN](https://ckan.org/), do qual fiz a primeira
tradução para o português ainda em 2009. O CKAN é o software livre usado nos
portais de dados abertos desses países e segue sendo o mais usado no mundo para
portais de dados abertos.

A ideia de que o governo federal deveria começar a oferecer dados abertos, como
já contei várias vezes (por exemplo, em
[2018](https://www.youtube.com/watch?v=Hl7vyxqKQEY) e em
[2020](https://www.youtube.com/watch?v=1rCsoU7XSdM)), surgiu de uma
[provocação feita pelo Pedro Markun, ativista do grupo Transparência Hacker, ao Cláudio Cavalcanti, então Coordenador-Geral de Gestão Corporativa na SLTI no Ministério do Planejamento, durante o evento Conip 2010](https://vimeo.com/12137194).

<figure markdown="1">
![Cláudio Cavalcanti e Pedro Markun discutem dados abertos em painel no evento Conip 2010.]({{ 'assets/images/2022/12/conip-2010-claudio-cavalcanti-pedro-markun.jpg' | relative_url }})
<figcaption>Cláudio Cavalcanti e Pedro Markun discutem dados abertos em painel no evento Conip 2010.</figcaption>
</figure>

Naquele momento também estava sendo gestada a
[Parceria para Governo Aberto](https://www.gov.br/cgu/pt-br/governo-aberto/a-ogp/o-que-e-a-iniciativa),
que promove a participação social na elaboração de políticas públicas.
Somando-se isto ao fato de que não dispúnhamos de recursos orçamentários
para a criação de um portal de dados abertos, decidimos elaborar tudo,
desde o portal até a própria estruturação da política pública, da forma
mais colaborativa e transparente possível.

<figure markdown="1">
![Uma das oficinas de planejamento da INDA durante o II Encontro Nacional de Dados Abertos, em 2013, facilitada por Alexandre Gomes.]({{ 'assets/images/2020/12/2enda-trilha-sustentabilidade-economica-alexandre-gomes.jpg' | relative_url }})
<figcaption>Uma das oficinas de planejamento da INDA durante o <a href="https://web.archive.org/web/20190511120800/http://wiki.dados.gov.br/II-Encontro-Nacional-de-Dados-Abertos.ashx" target="_blank">II Encontro Nacional de Dados Abertos</a>, em 2013, facilitada por Alexandre Gomes.</figcaption>
</figure>

[Todas as reuniões de planejamento e sprints de desenvolvimento](https://web.archive.org/web/20190512160325/http://wiki.dados.gov.br/Agenda-da-INDA.ashx)
eram abertas à participação de qualquer pessoa interessada, muitas vezes
realizadas fora do ambiente de governo em locais como cafés, documentadas
publicamente na internet e sempre que possível transmitidas por streaming –
isso em 2011, muitos anos antes de se tornar moda todo mundo transmitir
qualquer coisa por streaming – e com uma pessoa dedicada a trazer as interações
das pessoas online para o ambiente físico dos encontros.

<figure markdown="1">
![Encontro da 3ª sprint de desenvolvimento colaborativo do Portal Brasileiro de Dados Abertos, no Balaio Café, em 2011.]({{ 'assets/images/2022/12/3rd-sprint-open-data-portal-2011.jpg' | relative_url }})
<figcaption>Encontro da <a href="https://wiki-dados.cgu.gov.br/TerceiroRumblePortalDadosAbertos20110909.ashx" target="_blank">3ª sprint de desenvolvimento colaborativo do Portal Brasileiro de Dados Abertos</a>, no Balaio Café, em 2011.</figcaption>
</figure>

Todo esse processo tomou repercussão internacional bastante positiva. Afinal,
qual projeto de governo você conhece, em qualquer época, em qualquer lugar do
mundo, foram feitos dessa forma?
[Nesta página](https://web.archive.org/web/20210727185616/https://dados.gov.br/pagina/processo-de-participacao-social-da-inda)
há um relato bem detalhado do processo. Ainda bem que o Web Archive tem uma
cópia guardada do texto e das imagens, já que o conteúdo não está mais
disponível no local original (abordaremos mais detalhadamente mais adiante essa
indisponibilidade).

## Capacitação, normatização e ganhos de escala: 2016 a 2017

Apesar do sucesso em estabelecer de forma colaborativa o que seria
necessário fazer e criar um portal de dados abertos, a publicação de
dados abertos nos órgãos públicos ainda dependia do convencimento individual
de cada autoridade sobre a necessidade de patrocinar o processo. Faltava
um marco normativo, algo que buscávamos desde o início, mas até então
não havíamos conseguido apoio político suficiente para torná-lo
realidade.

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2020-12-07-open-data-a-committee-in-retrospect" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

Em 2012,
[o que foi possível fazer foi](https://web.archive.org/web/20190130151426/https://wiki.dados.gov.br/Marco-Normativo-da-INDA.ashx)
uma instrução normativa que instituía a Infraestrutura Nacional de Dados
Abertos -- INDA e o seu
[Comitê Gestor](https://web.archive.org/web/20181231213410/https://wiki.dados.gov.br/Comite-Gestor-da-INDA.ashx).
A história do Comitê Gestor já foi contada detalhadamente
[em outro texto neste blog]({{ reference_post.url | relative_url }}).

<figure markdown="1">
![Reunião do Comitê Gestor da INDA em 2016.]({{ 'assets/images/2020/12/cginda-2016.jpg' | relative_url }})
<figcaption>Reunião do Comitê Gestor da INDA em 2016.</figcaption>
</figure>

Porém, foi no apagar das luzes do governo Dilma, em 2016, que surgiu a
oportunidade de finalmente emplacar um decreto, como pretendíamos desde
o início. Foi o
[Decreto 8.777, de 11 de maio de 2016](http://www.planalto.gov.br/ccivil_03/_ato2015-2018/2016/decreto/d8777.htm),
que tornou obrigatório no poder executivo federal que cada órgão ou
entidade realizasse as suas publicações de dados abertos conforme um
plano estabelecido pela própria organização pública.

Porém, restava ainda o desafio de apoiar essas centenas de organizações
públicas a construir e colocar em prática esses planos. Com esse fim,
[capacitamos quase 1.800 pessoas](https://web.archive.org/web/20181216132407/http://wiki.dados.gov.br/Capacitacao-para-Elaboracao-de-Planos-de-Dados-Abertos.ashx)
sobre como elaborar Planos de Dados Abertos.

<figure markdown="1">
![Elise Gonçalves fala no III Seminário de Elaboração de Planos de Dados Abertos, no Rio de Janeiro.]({{ 'assets/images/2022/12/3rd-seminar-on-open-data-planning-rio-de-janeiro-2017.jpg' | relative_url }})
<figcaption>Elise Gonçalves fala no III Seminário de Elaboração de Planos de Dados Abertos, no Rio de Janeiro.</figcaption>
</figure>

Os resultados foram visíveis: de 1.167 conjuntos de dados em
[2016](https://web.archive.org/web/20190130145855/http://wiki.dados.gov.br/Balanco-da-INDA-em-2016.ashx),
o Portal Brasileiro de Dados Abertos passou a contar com 6.278 em
[2018](https://web.archive.org/web/20190130145906/http://wiki.dados.gov.br/Balanco-da-INDA-em-2018.ashx),
o que representa um incremento de 438% em dois anos. A quantidade de
órgãos públicos que publicavam dados no portal passaram  nesse período
de poucas dezenas para centenas de órgãos e entidades.

## "Cisma" do governo digital: 2018

Até então, tudo isso vinha sendo realizado no então Ministério do
Planejamento, Orçamento (ou Desenvolvimento, em certo período) e Gestão.
Em 2010, no contexto das políticas de interoperabilidade de dados do
governo federal, o e-PING, foi lá na então Secretaria de Logística e
Tecnologia da Informação -- SLTI, onde surgiram as condições para
colocar os dados, e o acesso a eles de forma automatizada, em primeiro
lugar.

Já em 2018 foi criada a Secretaria de Governo Digital, que levou toda a
estrutura que antes era voltada à interoperabilidade no governo. As
novas diretrizes eram claras: todos deveriam se focar na digitalização
de serviços públicos, na então plataforma de análise de dados do governo
chamada GovData, nas APIs internas de governo para governo ou na
simplificação do processo de abertura de empresas. Nas palavras do então
secretário, qualquer outro assunto que fosse alheio a estes (por
exemplo, dados abertos, software livre e software público) não teria
lugar na nova secretaria. Todos os servidores deviam trabalhar apenas
naqueles assuntos considerados prioritários.

### Transparência e dados abertos

Se a "casa" da política de dados abertos não podia mais ser o governo
digital, onde seria então? A primeira candidata natural seria a
Controladoria-Geral da União -- CGU que, desde a vigência do Decreto
8.777 em 2016 já exercia o papel de monitoramento e fiscalização dos
órgãos e entidades do poder executivo federal quanto ao cumprimento dos
seus respectivos Planos de Dados Abertos.

A CGU também era responsável pela política de transparência do governo
federal, tendo criado o Portal da Transparência ainda no ano de 2004.
Mas transparência e dados abertos são a mesma coisa? Se não, quais são
as diferenças?

De fato, há muitas semelhanças entre esses dois conceitos. Ambos visam a
dar conhecimento ao cidadão sobre algo que é produzido usando recursos
públicos, como forma de responsabilização (ou *accountability*, no termo
em inglês muito usado no jargão) pelo uso desses recursos.
São também uma forma de reduzir a disparidade de recursos de
informação e, consequentemente, de poder, entre o cidadão e o Estado.
Abrir dados também é uma forma de dar transparência ao funcionamento do
Estado.

<figure markdown="1">
![Mapa mental elaborado por Rodrigo Klein em sua tese, em 2017, apresenta as associações entre conceitos como governo aberto, transparência e dados abertos.]({{ 'assets/images/2022/12/mapa-mental-transparencia-dados-abertos-klein-2017.png' | relative_url }})
<figcaption>Mapa mental elaborado por Rodrigo Klein <a href="https://tede2.pucrs.br/tede2/handle/tede/7724" target="_blank">em sua tese</a>, em 2017, apresenta as associações entre conceitos como governo aberto, transparência e dados abertos.</figcaption>
</figure>

Todavia, há também diferenças tanto na origem normativa e conceitual,
quanto no público alvo e contexto de uso dos produtos dessas políticas.

A transparência vem da política de transparência fiscal, oriunda das
Leis Complementares n.º 101, de 2000, e
[131](https://www.planalto.gov.br/ccivil_03/leis/lcp/lcp131.htm), de
2009, que obrigaram todos os poderes e entes federativos (União,
Estados, Distrito Federal e Municípios) a terem os seus próprios portais
da transparência e neles publicar todas as receitas, despesas, orçamento,
licitações, etc. Isto é, a transparência fiscal está intimamente ligada
ao uso direto de recursos do erário e têm um enfoque em valores
financeiros.

Claro que a transparência, em um sentido mais amplo, abrange também **o
que se faz** e não apenas o **quanto se gasta** no setor público. Porém,
na prática, é bem menos comum ver esse tipo de informação nos portais da
transparência de entes públicos, provavelmente pelo fato de os requisitos
para tal não estarem mencionados explicitamente nos textos das leis.

Por exemplo, o registro das despesas é citado nominalmente tanto la LC
101 (art. 48-A, II), quanto na Lei de Acesso à Informação -- LAI (art.
8º, §1º, III). Todavia, dados um pouco mais específicos, como os
endereços e localização geográfica de todas as escolas e
estabelecimentos de saúde não são explicitamente citados em nenhuma lei.

A transparência também tradicionalmente tem como público alvo o cidadão
"médio", leigo, que não tem letramento de dados. Isto é, apresenta
análises prontas, elementos gráficos pré-concebidos e não tem muitas
opções nem condições para realizar suas próprias análises ou combinar os
dados com outros dados de outras fontes.

Com o expressivo aumento nos volumes de dados utilizados pela
administração pública na última década, tornou-se cada vez mais
necessário possibilitar que o próprio cidadão possa obter os dados e
realizar as suas próprias análises. As transformações na sociedade, cada
vez mais voltada ao digital, também alteraram o que seria o cidadão
"médio", uma vez que é cada vez mais comum que pessoas das mais diversas
profissões tenham conhecimentos mínimos para trabalhar diretamente com
dados.

É daí que surgiu a necessidade de "dados abertos" que empoderem o
cidadão a fazer seu próprio uso dos dados como bem entender, em vez de
ser "tutelado" pelos publicadores dos dados com análises prontas e
receber documentos em texto em formato PDF que dificultam até mesmo
realizar uma simples soma dos valores de uma coluna que estão em uma
tabela. É também sobre ter independência e autonomia.

A disponibilização de dados abertos de forma regular e confiável também
fomenta todo um ecossistema de serviços digitais que têm neles um insumo
fundamental. Entre outras tantas aplicações, sistemas de inteligência
artificial podem usar os dados para treinar seus modelos, por exemplo.
Diversos estudos têm apontado, inclusive,
[os impactos econômicos da disponibilização de dados abertos](https://www.europeandataportal.eu/sites/default/files/edp_creating_value_through_open_data_0.pdf)
e o seu papel
[no crescimento do produto interno bruto](https://www.omidyar.com/insights/open-business)
e
[no desenvolvimento sustentável](http://www.undatarevolution.org/report/)
das nações.

Ao contrário dos estados e
[dos municípios maiores](https://ok.org.br/noticia/indice-de-dados-abertos-de-dez-cidades-brasileiras-entra-na-fase-de-checagem-dos-dados/),
hoje em dia ainda é extremamente comum,
[especialmente em municípios menores](https://github.com/augusto-herrmann/transparencia-dados-abertos-brasil/),
encontrar portais da transparência que não oferecem dados abertos. Têm
apenas dados de receitas, despesas e licitações, frequentemente apenas
em documentos PDF.

A LAI, em 2011, já trouxe, em seu art. 8º, exigências de abertura de
dados, embora não utilizasse explicitamente o termo "dados abertos".
Mais tarde, também a Lei de Governo Digital, Lei n.º 14.129/2021 trouxe
exigências mais detalhadas de transparência ativa em seu art. 21.

Pode-se dizer que, do ponto de vista conceitual, "dados abertos" vem
geralmente associado à transparência, mas também como uma resposta às
lacunas existentes nas práticas vigentes até hoje. No mesmo passo,
percebe-se que as referências legislativas de dados abertos vêm todas
cerca de uma década depois das de transparência. Tampouco existe a
associação restritiva do conceito de dados abertos apenas com o aspecto
fiscal e financeiro: dados abertos são sobre todo e qualquer domínio do
conhecimento onde a organização atue. Onde se fala em dados abertos, é
bem mais comum ver dados bastante específicos sobre a operação de uma
determinada política pública, como, por exemplo
[a série histórica de preços dos combustíveis](https://dados.gov.br/dados/conjuntos-dados/serie-historica-de-precos-de-combustiveis-por-revenda).

Uma conclusão sobre essa comparação é que transparência e dados abertos
são conceitos que se complementam em vários aspectos, mas
definitivamente não são a mesma coisa. Entretanto, pensar dados abertos
apenas como mais uma forma de se atingir a finalidade da transparência é
limitar as suas potencialidades. Em especial, aquelas voltadas à
potencialização da economia digital.

### A transição

Com isso, a encomenda que recebi ao final de 2018 foi de preparar a
transição para que a CGU assumisse a responsabilidade pela política de
dados abertos no poder executivo federal, no lugar do Ministério da
Economia e da Secretaria de Governo Digital. Esse processo veio a
culminar no
[Decreto 9.903](http://www.planalto.gov.br/ccivil_03/_ato2019-2022/2019/decreto/D9903.htm),
de 2019. O Portal Brasileiro de Dados Abertos e a INDA, com seu Comitê
Gestor, também foram para a CGU, ficando o Ministério da Economia apenas
com um assento no comitê, com participação semelhante a diversos outros
ministérios.

## Os últimos 4 anos

Desde que recebeu a política de dados abertos,
[a equipe da CGU vem passando por sucessivas trocas de gestão](https://dadosabertos.social/t/cgu-assume-a-politica-de-dados-abertos-do-governo-federal/74/2).
O Comitê Gestor da INDA passou a se reunir com cada vez menor
frequência. Alteraram a norma que definia, até então,
[essa periodicidade com bimestral para ser apenas de quatro em quatro meses](https://dadosabertos.social/t/consulta-publica-sobre-a-infraestrutura-nacional-de-dados-abertos/373).
Porém, nem mesmo essa periodicidade foi cumprida: durante esses 4 anos,
[o Comitê se reuniu apenas 5 vezes](https://web.archive.org/web/20220823072104/https://wiki.dados.gov.br/%2fComite-Gestor-da-INDA.ashx).
Em 2022, apenas uma única vez, em maio.

As atividades da INDA se pautavam por um Plano de Ação. A CGU elaborou um
[Plano de Ação para o período 2021-2022](https://web.archive.org/web/20220620140753/https://wiki.dados.gov.br/Plano-de-Acao-da-INDA-2021-2022.ashx).
Porém,
[segundo o monitoramento feito pela Open Knowledge Brasil](https://dadosabertos.social/t/monitoramento-do-plano-de-acao-da-infraestrutura-nacional-de-dados-abertos-inda/910),
esse plano vem sendo alvo de sucessivos atrasos e adiamentos.

Quanto ao Portal Brasileiro de Dados Abertos, a CGU contratou, em 2021,
com apoio da Unesco,
[uma reestruturação](https://dadosabertos.social/t/reestruturacao-do-portal-brasileiro-de-dados-abertos/1007)
do mesmo. O portal já está no ar, mas
[os problemas se acumulam](https://dadosabertos.social/t/reestruturacao-do-portal-brasileiro-de-dados-abertos/1007/3).
Entre eles, a perda da memória do conteúdo histórico, tais como FAQs e
páginas explicativas dos conceitos de conjuntos de dados e dados
abertos, e também toda a wiki que continha os registros históricos de
como operava a INDA até 2018. Há também dificuldade de se encontrar na
nova interface os dados que se procura, já que os filtros de pesquisa
não se encontram facilmente encontráveis. O pior de tudo é a
indisponibilidade da API do CKAN, que muitos órgãos públicos utilizavam
para atualizar automaticamente os dados, inclusive o próprio Ministério
da Economia.

Antes mesmo dessa reformulação,
[outra integração importante que existia já havia sido quebrada](https://dadosabertos.social/t/fim-da-integracao-entre-o-dados-gov-br-e-o-fala-br-ouvidoria/570).
Antes de ir para a CGU, o portal tinha uma integração com o
sistema de ouvidoria do governo federal. Toda vez que qualquer pessoa
encontrasse um problema com um conjunto de dados, poderia enviar uma
reclamação que tramitaria pelo sistema de ouvidorias (inicialmente, pelo
sistema chamado e-Ouv, que depois passou a se chamar Fala.br). A
reclamação ia acompanhada, além da descrição do problema, também da URL
do conjunto de dados sobre o qual se estivesse reclamando, de forma a
melhorar a resolutividade, facilitando o trabalho da pessoa que fosse
responde a reclamação. Em 2020, essa integração parou de funcionar. Não
foi dada nenhuma explicação para a retirada da funcionalidade.

Além disso, todos os milhares de links para os conjuntos de dados
existentes antes da reforma do portal se tornaram imediatamente
quebrados. Não foi criado qualquer tipo de redirecionamento das URLs
antigas para as novas, como infelizmente é comum acontecer em qualquer
reformulação de portais de governo (sendo que, infelizmente, iniciativas
como o Web Archive nem sempre conseguem arquivar todo o conteúdo
antigo).

Um dos poucos pontos positivos foi a possibilidade de qualquer pessoa se
logar com a conta do gov.br e escrever comentários sobre cada conjunto
de dados específicos (por exemplo, em menos de uma semana em que é
possível comentar, já apareceu toda uma discussão sobre problemas de
qualidade ou dados corrompidos
[no dataset do CNPJ publicado pela Receita Federal](https://dados.gov.br/dados/conjuntos-dados/cadastro-nacional-da-pessoa-juridica-cnpj)).
No entanto, moderar os comentários em um portal dessa magnitude
certamente será um grande desafio -- motivo principal dessa funcionalidade
nunca ter estado disponível nas versões anteriores do portal.

A desassociação das políticas de dados abertos e de governo digital
também tem sido criticadas pela sociedade civil, tal como
[neste artigo](https://manualdousuario.net/podcast/tecnocracia-70/) de
Guilherme Felitti no blog Tecnocracia, com participação de Fernanda
Campagnucci, diretora executiva da Open Knowledge Brasil.

## Que venha 2023!

Esse período de 4 anos foi indiscutivelmente de poucos avanços e muitos
retrocessos para os dados abertos no governo federal. 

Com o novo governo provavelmente vêm novos gestores, e com eles novas
prioridades e novas ideias. Quem sabe nas próximas semanas possamos
discutir aqui e em outros lugares algumas delas.
