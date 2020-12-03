---
layout: post
title: "Dados abertos: a retrospectiva de um comitê"
author: "Augusto Herrmann"
lang: pt
ref: 2020-12-02-open-data-a-committee-in-retrospect
category: [pt, blog]
tags: [dados abertos,governo aberto,participação social]
cover: /assets/images/2020/12/maximilian-weisbecker-Esq0ovRY-Zs-unsplash.jpg
snippet-image: /assets/images/2020/12/cginda-2016.jpg
desc: >-
  Na última quinta, o Comitê Gestor da Infraestrutura Nacional de Dados
  Abertos se reuniu de novo, estando prestes a ser restabelecido após ter
  sido extinto há quase dois anos. O que podemos aprender ao rever a sua
  história?
image-credits: "Maximilian Weisbecker / Unsplash"
---

A possibilidade de se recriar um comitê de dados abertos no governo federal
brasileiro me levou a lembrar e a contar a história do comitê de dados
abertos que nós criamos oito anos atrás. Por favor tenha em mente, todavia,
que esta não é a história completa da Infraestrutura Nacional de Dados
Abertos (INDA), ou mesmo as suas partes mais importantes, mas sim somente
a parte que envolve o comitê e os assuntos que foram nele discutidos ao
longo dos anos.

## Inspiração e motivação

Em 2011, quando estávamos projetando a política de dados abertos do governo
federal brasileiro, um dos desafios que encaramos foi como se certificar que
cidadãos e cidadãs tivessem um lugar e pudessem opinar sobre como a política
seria conduzida. Um modelo para nós foi o
[Comitê Gestor da Internet](https://cgi.br/) (CGI.br).

Estabelecido em 1995, o CGI.br tem
[representantes de múltiplos setores da sociedade](https://cgi.br/membros/):
governo, empresas, terceiro setor, a comunidade de ciência e tecnologia e
um especialista em internet. Se por um lado os representantes do governo
são nomeados diretamente, os representantes setoriais são escolhidos por
voto dos entes jurídicos de cada respectivo setor. O especialista em
internet é nomeado pelo Ministério da Ciência e Tecnologia. Essas regras
estão detalhadas no
[Decreto n.º 4.829](http://www.planalto.gov.br/ccivil_03/decreto/2003/d4829.htm),
de 2003.

<figure markdown="1">
![Gráfico mostrando a composição dos membros do CGI.br: 9 do governo, 4 do setor privado, 4 do terceiro setor, 3 da comunidade de ciência e tecnologia e um especialista em internet.]({{ 'assets/images/2020/12/cgi-membros.gif' | relative_url }})
<figcaption>Composição dos membros do CGI.br (fonte: <a target="_blank" href="https://cgi.br/membros/">site do CGI.br</a>).</figcaption>
</figure>

O CGI.br foi escolhido como modelo principalmente porque ele é visto como
um exemplo de sucesso de boa governança multissetorial em assuntos
tecnológicos e sociais, como já era o caso por mais de uma década, à
época. Além disso, as autoridades na então Secretaria de Logística e
Tecnologia da Informação (SLTI) já tinham experiência direta de participação
nele, já que a SLTI tinha assento no CGI.br, então era uma ideia fácil de
se vender aos superiores.

Todavia, como não tínhamos qualquer orçamento dedicado à iniciativa de
dados abertos que acabara de começar, algumas concessões tiveram que ser
feitas. O CGI.br sempre dispôs de recursos porque parte das taxas de
registro pagas para o registrador TLD do .br por pessoas e organizações
que querem registrar um nome de domínio vão para financiar o
[Núcleo de Informação e Coordenação do Ponto BR](https://nic.br/sobre/)
(NIC.br), que provê o suporte operacional para o CGI.br, assim como outras
operações relacionadas, como o
[próprio registrador](http://registro.br/) (registro.br), o
[Centro Regional de Estudos para o Desenvolvimento da Sociedade da Informação](https://www.cetic.br/pt/sobre/)
(CETIC.br)
e o [escritório regional do W3C no Brasil](https://www.w3c.br/Sobre/)
(W3C.br).

Nós, por outro lado, não tivemos essa sorte em garantir recursos para a
iniciativa. Além disso, nós tentamos, à época, que a política de dados
abertos fosse estabelecida por um decreto, como é o caso do CGI.br, mas
a força política do movimento de dados abertos no governo era suficiente
apenas para obter uma instrução normativa. Por isso, tivemos que
simplificar um pouco a estrutura de governança. O
[Comitê Gestor da Infraestrutura Nacional de Dados Abertos](https://wiki.dados.gov.br/Comite-Gestor-da-INDA.ashx)
(CGINDA) foi instituído pela
[Instrução Normativa n.º 4, em 2012](https://dados.gov.br/pagina/instrucao-normativa-da-inda),
com representantes de nove órgãos e entidades de governo, um
representante da sociedade civil, que seria nomeado pela Secretaria
Nacional de Articulação Social, e um representante do setor acadêmico, a
ser nomeado pelo Ministério da Ciência, Tecnologia e Inovação (MCTI).
Isso significava que não seriam realizadas eleições para os representantes,
o que é pior para a participação quando comparado ao CGI.br, mas também
significava que não teríamos que arcar com os custos de uma eleição sem
ter recursos para isso. Isso também queria dizer que o comitê poderia
começar a trabalhar imediatamente e fazer rapidamente com que as coisas
começassem a funcionar. O apoio operacional para o funcionamento do
comitê seria oferecido pela SLTI, que também o presidiria.

<figure markdown="1">
[![Christian Miranda apresenta o então atual estado do plano]({{ 'assets/images/2020/12/acompnhamento-da-inda-04-2011.jpg' | relative_url }})](https://www.youtube.com/watch?v=poN5cIQPz-8)
<figcaption>Christian Miranda apresenta o então atual estado do plano para
instituir a INDA em abril de 2011, em um dos poucos registros em vídeo
existentes do início da história da INDA. O vídeo completo está
<a target="_blank" href="https://www.youtube.com/watch?v=poN5cIQPz-8">disponível no Youtube</a>.
</figcaption>
</figure>

Naquela época, o planejamento da iniciativa já estava sendo elaborado
colaborativamente por servidores públicos interessados e pessoas motivadas
da sociedade civil, como pode ser visto nos registros do
[workshop de planejamento em março](https://wiki.dados.gov.br/I-Workshop-de-Planejamento-da-INDA.ashx)
e reuniões subsequentes ocorridas em
[abril](https://wiki.dados.gov.br/Reuniao-de-Acompanhamento-do-Planejamento-da-INDA-em-19-04-2011.ashx),
[maio](https://wiki.dados.gov.br/Verificacao-e-Aprovacao-do-Plano-de-Trabalho-da-INDA-2011-05-11.ashx)
e
[julho](https://wiki.dados.gov.br/Reuniao-de-acompanhamento-do-plano-de-projeto-2011-07-12.ashx),
bem como a audiência pública da instrução normativa ocorrida em outubro,
durante o I Encontro Nacional de Dados Abertos.
Então era natural esperar que a estrutura do comitê fosse ter uma composição
semelhante à participação que já vinha ocorrendo desde o início de 2011.

<figure markdown="1">
![Um painel de autoridades abre o evento diante do auditório cheio]({{ 'assets/images/2020/12/1-encontro-nacional-de-dados-abertos.jpg' | relative_url }})
<figcaption>A abertura do <a target="_blank" href="https://wiki.dados.gov.br/I-Encontro-Nacional-de-Dados-Abertos.ashx">I Encontro Nacional de Dados Abertos</a>,
ocorrido em Brasília, em outubro de 2011.</figcaption>
</figure>

## Primeiras reuniões

Apesar do CGINDA ter sido estabelecido em abril de 2012, as nomeações de
representantes pelos ministérios e entidades públicas demorou um pouco a
acontecer. Portanto, a
[primeira reunião](https://wiki.dados.gov.br/GetFile.aspx?File=%2fComiteGestor%2fAtas%2fAta%20da%201a%20reuni%c3%a3o%20do%20Comit%c3%aa%20Gestor%20da%20INDA%2001-10-12.odt)
aconteceu somente em outubro. Como ainda era uma novidade para todos os
envolvidos, foram explicados ali a recente Instrução Normativa n.º 4 e
os detalhes de como o CGINDA iria operar. O outro grande tópico foi o
primeiro
[Plano de Ação da INDA](https://wiki.dados.gov.br/Plano-de-Acao-da-INDA.ashx),
que se baseou na experiência do plano originalmente construído
colaborativamente no workshop de março de 2011. Percebia-se uma necessidade
ao mesmo tempo de discutir extensivamente o plano e também de lançá-lo
rapidamente, então a próxima reunião foi em novembro, apesar da periodicidade
prevista para as reuniões ser bimestral. Entretanto os frequentes pedidos
de ajustes significaram que a aprovação formal do plano pelo CGINDA só viria
a ocorrer em fevereiro de 2013. Aquele
[Plano de Ação](https://wiki.dados.gov.br/Plano-de-Acao-da-INDA-2013-2014.ashx)
abarcou o período 2013-2014.

Essa primeira fase do comitê foi marcada por discussões sobre como
ampliar a participação nele da sociedade civil. A professora Gisele
Craveiro, da Universidade de São Paulo, representante da sociedade civil
em nome da Open Knowledge Brasil, frequentemente trouxe à luz a
necessidade de transmitir as reuniões pela internet, para que mais
pessoas pudessem assistir e participar. Pode parecer incomum para a
época e também para hoje que as discussões pudessem acontecer
abertamente dessa maneira, mas era isso que as pessoas esperavam de nós.
Tínhamos acabado de terminar de construir o Portal Brasileiro de Dados
Abertos
[de uma maneira totalmente aberta e participativa](https://dados.gov.br/pagina/processo-de-participacao-social-da-inda),
diferente de qualquer coisa que tivesse sido feita no mundo antes. Logo,
formas de ampliar a participação da sociedade foi uma das questões que
estavam sendo discutidas relacionadas ao
[regimento interno](https://wiki.dados.gov.br/GetFile.aspx?File=%2fComiteGestor%2fResolu%c3%a7%c3%b5es%2fresolucao-cginda-1-24-3-2017%2cpdf.pdf),
o qual acabaria por ser terminado e aprovado formalmente pelo comitê somente
em 2017.

Também foram discutidos em muitas reuniões naquele tempo o monitoramento
e execução do Plano de Ação da INDA e também as partes do Plano de Ação
Nacional de Governo aberto que se relacionavam com dados abertos.
O Brasil havia sido um dos fundadores da
[Parceria para Governo Aberto](https://www.gov.br/cgu/pt-br/governo-aberto/a-ogp/o-que-e-a-iniciativa)
em 2011 e, desde o início, todos os planos de ação sempre contiveram
compromissos relacionados a dados abertos.

## Ganhando velocidade e indo adiante

A reunião do CGINDA de novembro de 2013 inaugurou uma nova fase no comitê.
O MCTI, que até então não havia nem participado, nem indicado o representante
do setor acadêmico, começou a comparecer regularmente. Muitos assuntos
relevantes foram discutidos, naquele momento, no comitê:
* o
  [II Encontro Nacional de Dados Abertos](https://wiki.dados.gov.br/II-Encontro-Nacional-de-Dados-Abertos.ashx),
  que se aproximava, e a hackatona de dados abertos que aconteceu durante
  ele;
* como lidar com as licenças de dados heterogêneas, que já estavam
  presentes no portal de dados abertos (que motivou, mais tarde, um
  [estudo sobre o assunto](https://wiki.dados.gov.br/Produto-GT1-Levantamento-Juridico-Licenciamento-Dados-Abertos.ashx));
* uma possível rede de capacitação sobre dados abertos, com o apoio do W3C.br
  (que infelizmente nunca se concretizou na forma de rede, apesar de que
  [ofertamos cursos para milhares de pessoas](https://wiki.dados.gov.br/Capacitacao-da-INDA.ashx)
  na administração pública, em assuntos relacionados a dados abertos, ao
  longo dos anos, em parceria com a Enap, a escola da administração pública);

e mais.

<figure markdown="1">
[![Vagner Diniz, Valter Correia e Míriam Chaves apresentam para uma casa cheia no evento no auditório do Ministério do Planejamento]({{ 'assets/images/2020/12/gestao-em-destaque-dados-abertos-2013.jpg' | relative_url }})](https://www.youtube.com/watch?v=D3CeB1HFq0U)
<figcaption>Os resultados do momento foram apresentados no evento "Gestão em Destaque" no Ministério do planejamento, em setembro de 2013. O vídeo completo está <a target="_blank" href="https://www.youtube.com/watch?v=D3CeB1HFq0U">disponível no Youtube</a>.</figcaption>
</figure>

O II Encontro Nacional de Dados Abertos, que recebeu quase 300
participantes ao longo de dois dias em novembro de 2013, foi muito
importante e fortemente influenciador na história dos dados abertos no
Brasil. Praticamente todos os palestrantes desta conferência viriam mais
tarde a desempenhar um papel ainda mais importante, de alguma maneira,
no desenvolvimento do ecossistema de dados abertos nos anos
subsequentes. There were not only talks, but also courses, workshops on
topics very much relevant to the open data agenda and an open data
contest that awarded applications that used open data for developing
civic applications.

Os temas das oficinas foram:

* a sustentabilidade econômica dos dados abertos;
* estudos de casos locais de abertura de dados em estados e municípios;
* educação e dados abertos;
* privacidade e proteção de dados pessoais;
* licenciamento de dados abertos.

<figure markdown="1">
![Alexandre Gomes media as discussões na oficina de sustentabilidade econômica dos dados abertos]({{ 'assets/images/2020/12/2enda-trilha-sustentabilidade-economica-alexandre-gomes.jpg' | relative_url }})
<figcaption>Alexandre Gomes media as discussões em uma das oficinas,
sobre a sustentabilidade econômica dos dados abertos, durante o
<a target="_blank" href="https://wiki.dados.gov.br/II-Encontro-Nacional-de-Dados-Abertos.ashx">
II Encontro Nacional de Dados Abertos</a>, em Brasília, em novembro de 2013.</figcaption>
</figure>

Depois de uma contextualização por especialistas em cada assunto, os
participantes da oficina foram convidados a discutir, colaborar e construir
uma proposta para ajustar os rumos da política de dados abertos. Essas
propostas foram então apresentadas na
[reunião seguinte do CGINDA em janeiro de 2014](https://wiki.dados.gov.br/GetFile.aspx?File=%2fComiteGestor%2fAtas%2fAta%20da%208a%20reuniao%20ordinaria%20do%20Comite%20Gestor%20da%20INDA%202014-01-22.odt).
Essa foi mais uma maneira de avançar a participação social na iniciativa de
dados abertos.

## Preparativos para o crescimento

Também em 2014 veio a primeira prova de conceito de um Plano de Dados
Abertos institucional, mostrado no CGINDA. Ele propunha um conjunto de
compromissos que o Ministério do Planejamento, Orçamento e Gestão
assumiria em abrir certos conjuntos de dados, até uma determinada data
limite e uma indicação de quem seria responsável por cada um deles. Esse
tipo de plano iria mais tarde se tornar instrumental para expandir a
política de dados abertos para todos os órgãos públicos. Na época, a
situação mais comum era que algumas instituições com pessoas engajadas
estavam à frente da curva ao publicar alguns dados abertos, enquanto
outras instituições estavam paradas. Então, um instrumento para tornar a
publicação de novos dados abertos um processo regular e organizado era
algo altamente necessário.

A partir do fim de 2014 e durante o ano de 2015, o progresso se tornou
lento. Apesar de todos os avanços nos anos anteriores, relativamente
poucas instituições se engajavam ativamente na publicação de dados no
Portal Brasileiro de Dados Abertos. Tudo dependia da existência em cada
instituição governamental de algumas pessoas chave que estivessem
convencidas e engajadas com a ideia, já que não havia muito o que
compelisse essas instituições a fazê-lo. A despeito do fato da Lei de
Acesso à Informação, promulgada em 2011, exigir, no art. 8º que a
informação fosse disponibilizada como dados abertos, raramente isso se
traduziria na prática. Na época, a gestão da iniciativa também se tornara
altamente carente de pessoal, às vezes contando com uma única pessoa
(eu mesmo). Foi também nesse momento que a política de dados abertos foi
objeto de uma
[auditoria do Tribunal de Contas da União](https://www.lexml.gov.br/urn/urn:lex:br:tribunal.contas.uniao;plenario:acordao:2016-11-16;2904)
(TCU).

Outro problema era que alguns dos principais repositórios de dados
de instituições importantes ainda não estavam integrados ao Portal
Brasileiro de Dados Abertos, como a
[Infraestrutura Nacional de Dados Espaciais](https://www.inde.gov.br/)
(INDE). O desafio técnico de tornar esses dados geoespaciais disponíveis
também no Portal Brasileiro de Dados Abertos foi implementado nesse
período.

Esse tempo também foi útil para avaliar e monitorar a implementação do
Plano de Dados Abertos do Ministério do Planejamento, que estava em curso.
O plano viria a se tornar um modelo para que outros órgãos e entidades
governamentais fizessem os seus próprios planos institucionais, tal como
o Ministério da Justiça logo seguiria publicando o seu próprio plano de
dados abertos.

Também foi naquele período que começamos a elaborar relatórios anuais
sobre o progresso da política de dados abertos. Os relatórios de 
[2014](https://wiki.dados.gov.br/Balanco-da-INDA-em-2014.ashx) e
[2015](https://wiki.dados.gov.br/Balanco-da-INDA-em-2015.ashx) eram
bastante simples, mas eles se tornaram mais elaborados e detalhados ao
longo dos anos.

## Ganhando escala para os dados abertos em todas as instituições federais

Em 2016, finalmente vimos a oportunidade de fazer com que os dados abertos
ganhassem escala para todas as instituições do governo federal. Um dos
últimos atos assinados pela presidente Dilma Rousseff, o
[Decreto n.º 8.777/2016](http://www.planalto.gov.br/ccivil_03/_Ato2015-2018/2016/Decreto/D8777.htm)
estabeleceu que planos de dados abertos institucionais, como os que tinham
sido feitos no Ministério do Planejamento e no Ministério da Justiça, se
tornaria obrigatório para todos os órgãos e entidades federais:

> § 2º A implementação da Política de Dados Abertos ocorrerá por meio da
> execução de Plano de Dados Abertos no âmbito de cada órgão ou entidade
> da administração pública federal, direta, autárquica e fundacional, o
> qual deverá dispor, no mínimo, sobre os seguintes tópicos:
>
> I - criação e manutenção de inventários e catálogos corporativos de
> dados;
>
> II - mecanismos transparentes de priorização na abertura de bases de
> dados, os quais obedecerão os critérios estabelecidos pela INDA e
> considerarão o potencial de utilização e reutilização dos dados tanto
> pelo Governo quanto pela sociedade civil;
>
> III - cronograma relacionado aos procedimentos de abertura das bases
> de dados, sua atualização e sua melhoria;
>
> IV - especificação clara sobre os papeis e responsabilidades das
> unidades do órgão ou entidade da administração pública federal
> relacionados com a publicação, a atualização, a evolução e a
> manutenção das bases de dados;
>
> V - criação de processos para o engajamento de cidadãos, com o
> objetivo de facilitar e priorizar a abertura da (sic) dados, esclarecer
> dúvidas de interpretação na utilização e corrigir problemas nos dados
> já disponibilizados; e
>
> VI - demais mecanismos para a promoção, o fomento e o uso eficiente e
> efetivo das bases de dados pela sociedade e pelo Governo. 

Fazer com que mais de 200 instituições públicas elaborem os seus próprios
planos assim, em tempo hábil, não foi uma tarefa fácil. Algumas das
principais medidas que tornaram isso possível foram:

* capacitação:
  * usar os
    [primeiros planos de dados abertos](https://dados.gov.br/noticia/ministerio-do-planejamento-divulga-plano-de-dados-abertos-pda)
    como exemplos e modelos para elaborar novos planos;
  * disponibilizar um
    [manual de elaboração do plano](https://wiki.dados.gov.br/GetFile.aspx?File=%2fManuais%2fPlanos%20de%20Dados%20Abertos%2f2018%2fManual%20de%20Elaboracao%20de%20Planos%20de%20Dados%20Abertos.pdf&AsStreamAttachment=1&Provider=ScrewTurn.Wiki.FilesStorageProvider&NoHit=1)
    detalhado, com instruções passo a passo;
  * oferecer extensivamente
    [cursos sobre como elaborar o plano](https://wiki.dados.gov.br/Capacitacao-para-Elaboracao-de-Planos-de-Dados-Abertos.ashx);
  * visitar as instituições de “porta em porta” e oferecer ajuda para
    superar obstáculos;
* comunicação:
  * mostrar os primeiros planos mais bem feitos como exemplos positivos
    para que outros sigam;
  * certificar-se de que todas as organizações sejam notificadas do que e
    de como elas precisam fazer;
* monitoramento:
  * a Controladoria-Geral da União (CGU), que já era responsável por auditar
    a administração federal, recebeu a atribuição naquele decreto de
    monitorar o progresso dessas organizações na elaboração e implementação
    desses planos de dados abertos institucionais.

Para encarar esse grande desafio, a equipe que atuava na gestão da política
de dados abertos foi aumentada para seis pessoas. Alguns investimentos
essenciais também foram feitos ao oferecer cursos que capacitaram quase 800
servidores públicos com oficinas presenciais e quase 1.800 pessoas no
curso à distância.

<figure markdown="1" class="text-wide">
![uma das sessões de capacitação para servidores públicos sobre como planejar dados abertos]({{ 'assets/images/2019/11/open-data-planning-traning.jpg' | relative_url }})
<figcaption>Uma das oficinas de planejamento de dados abertos para servidores públicos no governo federal.</figcaption>
</figure>

Além dos planos de dados abertos terem sido o foco principal durante 2016 e
2017, algumas normas foram deliberadas e aprovadas pelo CGINDA:

* o próprio regimento interno do comitê,
* os termos de uso do Portal Brasileiro de Dados Abertos,
* [uma resolução](https://wiki.dados.gov.br/GetFile.aspx?File=%2fComiteGestor%2fResolu%c3%a7%c3%b5es%2fresolucao-cginda-3-13-10-2017.pdf)
  sobre como elaborar o plano de dados abertos institucional.

Muitos outros assuntos também foram discutidos, como: a revisão do padrão
de metadados em face de novos padrões internacionais como o
[DCAT](https://www.w3.org/TR/vocab-dcat-2/) do W3C e os
[perfis de aplicaçao](https://joinup.ec.europa.eu/asset/dcat_application_profile/description)
nacionais usados pela União Europeia, a auditoria do TCU em andamento, os
compromissos de dados abertos no Plano de Ação Nacional de Governo Aberto,
a participação em conferências internacionais sobre dados abertos e outros
intercâmbios internacionais, boas práticas na proteção de dados pessoais
antes de abrir os dados, como tratar os dados geoespaciais e os padrões de
metadados relacionados, acordos com outros níveis de governo para federar
portais de dados abertos e outros.

<figure markdown="1">
![Representantes do comitê reunidos em volta de uma mesa assistem a uma apresentação]({{ 'assets/images/2020/12/cginda-2016.jpg' | relative_url }})
<figcaption>Representantes do CGINDA se juntam para a 15ª reunião, em novembro
de 2016.</figcaption>
</figure>

Um tópico recorrente também foi a colocação do Brasil em rankings
internacionais de dados abertos, principalmente o
[Open Data Index](https://index.okfn.org/place/br/) e o
[Open Data Barometer](https://opendatabarometer.org/country-detail/?_year=2017&indicator=ODB&detail=BRA).
Eu sempre despendi o tempo para responder às pesquisas e questionários,
para procurar dados e outras evidências do que já estava disponível e
certificar-me de que elas estavam presentes nas respostas. Uma deficiência
óbvia sempre foi em encontrar evidências dos impactos sociais e econômicos.
Empresas que usam dados abertos frequentemente não revelam as suas fontes
de dados, por isso é necessário algum investimento em realizar pesquisas
com elas. Outros países na América Latina, como o México, já haviam
investido em pesquisar quais empresas privadas usam os dados abertos,
realizadas em estudos de caso no
[Open Data 500 do GovLab](https://thegovlab.org/project/project-open-data-500-global-network).
Eu já estava levando à atenção do comitê que os impactos sociais e
econômicos dos dados abertos no Brasil teriam que ser medidos e que ações
teriam que ser realizadas para melhorar esses impactos. Mais sobre os
impactos dos dados abertos serão assunto de outra postagem minha.

## Pisando no freio e transição para uma nova gestão

Já em 2018, a priorização da transformação digital de serviços foi a razão
alegada pelas novas autoridades para decidir se abster da responsabilidade
pela gestão da iniciativa e transferi-la à CGU. O órgão esteve, até então,
responsável apenas por monitorar e auditar as instituições federais em sua
implementação da política de dados abertos. A CGU também havia sido
responsável, há muito tempo, pela política de transparência do governo
federal. O portal da transparência havia sido inaugurado em 2004, embora
os downloads de dados estruturados tenham vindo muito mais tarde. Na visão
desses tomadores de decisão, os dados abertos promovem a transparência,
por isso os esforços seriam melhor concentrados se a liderança da política
de dados abertos também estivesse nas mãos da CGU.

Esse é uma linha de pensamento válida. Todavia, pode-se argumentar que
dados abertos não é apenas sobre transparência. Pessoas e organizações da
sociedade civil podem usar os dados abertos para construir novas soluções
para problemas sociais. Empresas podem usar os dados abertos para criar
novos modelo de negócios inovadores e também melhorar a eficiência dos
existentes.Pesquisas revelaram
[várias](https://www.mckinsey.com/business-functions/mckinsey-digital/our-insights/open-data-unlocking-innovation-and-performance-with-liquid-information)
e
[reiteradas](https://www2.deloitte.com/content/dam/Deloitte/uk/Documents/deloitte-analytics/open-data-driving-growth-ingenuity-and-innovation.pdf)
[vezes](https://lateraleconomics.com.au/wp-content/uploads/omidyar_open_business.pdf)
como os dados abertos podem impactar até mesmo indicadores macroeconômicos
como o PIB, criar empregos e reduzir os gastos governamentais com ganhos
de eficiência. Faria sentido mantê-la no recém criado Ministério da
Economia, onde já estava, porque esses eram os aspectos da política de
dados abertos que mais precisavam ser melhorados.

Entretanto, a decisão estava tomada. O pessoal foi realocado em outros
projetos e nenhum investimento subsequente na política de dados abertos ou
no portal seria permitida até que a transição estivesse concluída. Fui
encarregado da tarefa de elaborar um novo decreto que iria efetivar essa
decisão. Isso eventualmente se tornou o
[Decreto n.º 9.903/2019](http://www.planalto.gov.br/ccivil_03/_Ato2019-2022/2019/Decreto/D9903.htm).

Aproveitei a oportunidade para tratar
[um problema de longa data](https://www.ok.org.br/noticia/dados-meio-abertos-sobre-o-uso-e-reuso-dos-dados-governamentais-brasileiros/),
o fato de que diferentes organizações no governo ou escolhiam licenças
abertas diferentes ou simplesmente não definiam licença nenhuma. Definindo
uma licença aberta automática para todo o governo federal, não seria mais
necessário que gestores de bases de dados tivessem que decidir sobre
licenças de uma forma individual. Quaisquer diretos sobre bases de dados
que pudessem se aplicar a conjuntos de dados que fossem abertos seriam
[automaticamente autorizados](https://dadosabertos.social/t/governo-federal-esta-proibido-de-utilizar-cc-nc/375/2)
para uso do público.

> Art. 1º O Decreto nº 8.777, de 11 de maio de 2016, passa a vigorar com
> as seguintes alterações:
> 
> > “Art. 4º Os dados disponibilizados pelo Poder Executivo federal e as
> > informações de transparência ativa são de livre utilização pelos
> > Poderes Públicos e pela sociedade.
> > 
> > § 1º Fica autorizada a utilização gratuita das bases de dados e das
> > informações disponibilizadas nos termos do disposto no inciso XIII
> > do caput do art. 7º da Lei nº 9.610, de 19 de fevereiro de 1998, e
> > cujo detentor de direitos autorais patrimoniais seja a União, nos
> > termos do disposto no art. 29 da referida Lei.
> > 
> > § 2º Fica o Poder Executivo federal obrigado a indicar o detentor de
> > direitos autorais pertencentes a terceiros e as condições de utilização
> > por ele autorizadas na divulgação de bases de dados protegidas por
> > direitos autorais de que trata o inciso XIII do caput do art. 7º da
> > Lei nº 9.610, de 1998.” (NR)

A desaceleração da iniciativa significava, entretanto, que o comitê viria
a se reunir somente três vezes em 2018. No início de 2019, o que já estava
devagar parou totalmente quando o CGINDA foi extinto pelo
[Decreto n.º 9.759/2019](http://www.planalto.gov.br/ccivil_03/_ato2019-2022/2019/decreto/d9759.htm),
juntamente com diversos outros comitês e conselhos.

Os planos de dados abertos e novos conjuntos de dados não pararam,
entretanto, já que o Decreto 8.777/2016 ainda estava em vigor, exigindo
que as instituições governamentais o fizessem. Entretanto, não havia mais
Plano de Ação da INDA em vigor e nem lugar para discutir com a sociedade
o que era importante fazer com a política de dados abertos no nível
federal.

## Um novo começo para o comitê?

Em maio deste ano, a CGU
[colocou em consulta pública](https://www.gov.br/cgu/pt-br/governo-aberto/noticias/2020/5/consulta-publica-sobre-reestruturacao-da-infraestrutura-nacional-de-dados-abertos-esta-disponivel)
uma nova norma que substituiria a Instrução Normativa n. 4 e reinstituiria
o CGINDA com uma nova composição. A proposta aumentaria o número de
representantes da sociedade civil no comitê para cinco: dois de organizações
que trabalhem com fomento à transparência e dados abertos, dois de grupos
de pesquisa e um do setor privado. Ela também reduz a frequência das
reuniões para uma a cada quatro meses, juntamente com
[diversas outras mudanças menores](https://dadosabertos.social/t/consulta-publica-sobre-a-infraestrutura-nacional-de-dados-abertos/373).
Na proposta que veio a consulta pública, todos esses cinco representantes
da sociedade civil seriam nomeados pela própria CGU. Considerando o
histórico do movimento dos dados abertos, bem como as discussões anteriores
sobre o assunto dentro do próprio comitê, seria aconselhável que alguma
forma de eleições entre os pares, como o CGI.br sempre fez, fosse o método
preferido de escolher os representantes.

Não há Plano de Ação da INDA vigente atualmente e a elaboração de um novo
plano já foi afirmada como sendo uma das primeiras prioridades da CGU. Ao
fazê-lo, deveria haver também alguma forma de participação social. Afinal,
como Thiago Rondon certa vez ponderou,
[o movimento dos dados abertos tem uma arquitetura de participação](https://www.ok.org.br/noticia/o-movimento-de-dados-abertos-tem-uma-arquitetura-de-participacao/).
