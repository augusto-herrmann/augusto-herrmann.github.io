---
layout: post
title: >-
  Concordar sob coerção não é consentimento: como o Estado contribui
  para nos subjugar às Big Tech
author: Augusto Herrmann
lang: pt
ref: 2025-04-27-agreeing-under-coercion-is-not-consent-how-the-state-does-contribute-to-subjugate-us-to-big-tech
category: [pt, blog]
tags: [dados pessoais, big tech, zero rating, termos de serviço, aplicativos]
cover: /assets/images/2025/04/cytonn-photography-GJao3ZTX9gU-unsplash.jpg
snippet-image: /assets/images/2025/04/cytonn-photography-GJao3ZTX9gU-unsplash.jpg
desc: >-
  Acostumamo-nos a aceitar os termos de serviço sem ler, cedendo os dados
  e poder às poucas grandes empresas que controlam a internet. O pior de
  tudo é que o poder estatal, em alguns países, em especial o Brasil, tem
  contribuído para agravar essa situação, ao condicionar o exercício de
  deveres e a efetivação de direitos à aceitação pelo cidadão das exigências
  das grandes plataformas. Saiba como podemos resistir e o que podemos fazer
  para tentar reverter essa situação.
image-credits: Cytonn Photography / Unsplash
---

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2021-08-10-my-discord-with-discord-or-choosing-alternatives-with-better-terms-of-service" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

Há muitos anos as pessoas têm sido condicionadas a marcar a caixa ou
clicar o botão, sem ler, afirmando que concordam com os "termos de serviço"
e "política de privacidade" de todo serviço online que deseje utilizar,
sem refletir por um segundo sequer nas suas consequências. O diabo está
nos detalhes pois, muitas vezes, nas letrinhas miúdas escondem-se práticas
de uso de dados pessoais, as quais se fossem lidas, a pessoa provavelmente
não concordaria. Como, por exemplo, o compartilhamento de dados pessoais
com parceiros, para fins de marketing e outros fins não especificados.

Muitas vezes a pessoa não tem a opção de não concordar, por diversos
motivos. Por exemplo, por pressão social, considerando que todo o seu
círculo social usa o mesmo aplicativo de mensagens ou rede social. Ou
mesmo porque as empresas com as quais a pessoa precisa se relacionar só
usam um determinado aplicativo de mensagens, sem o qual a relação de
consumo torna-se impossível. Nesses casos, a pessoa pode tentar procurar
um concorrente que utilize um aplicativo diferente, mas nem sempre isso é
possível, pois na maioria das vezes todas as empresas usam o mesmo
aplicativo, sempre das poucas empresas chamadas
"[*Big Tech*](https://pt.wikipedia.org/wiki/GAFAM)" que detêm um
monopólio ou um oligopólio do setor.

No caso do Brasil, por exemplo, estabeleceu-se um monopólio *de facto* do
WhatsApp, especialmente desde que a empresa Meta, dona do aplicativo,
começou a pagar as operadora de internet móvel pelo privilégio de excluir
somente os seus aplicativos da franquia da internet móvel, em detrimento
dos demais. No Brasil, os planos de internet móvel possuem limitações de
volume de tráfego de dados. Se a pessoa usar qualquer outro aplicativo de
mensagens, como o Signal ou Element, vai logo gastar o seu limite. Por
outro lado, se usar o WhatsApp, não gasta nada. É o chamado *zero-rating*.
É exatamente esse desequilíbrio de mercado que levou à dominância desse
aplicativo no Brasil, onde quase 100% das pessoas usam e cria-se uma
expectativa social e comercial de que todo mundo precisa usá-lo.

Essa distorção de mercado chegou a ser avaliada entre 2015 e 2018 pelo
[Conselho Administrativo de Defesa Econômica – CADE](https://www.gov.br/cade/pt-br),
órgão governamental que tem por objetivo a defesa da concorrência, que
decidiu arquivar o caso após manifestação da
[Anatel](https://www.gov.br/anatel/pt-br), com argumentação contrária a
qualquer lógica, de que a isenção de franquia ampliaria a concorrência e
estimularia a inovação. Dez anos depois, sabemos bem qual foi o
resultado. Entretanto, essa é uma história que contarei em detalhes em
outro texto. Na ocasião, mostrarei quem foram as partes envolvidas, os
argumentos e previsões que elas fizeram e o contraste com o que de fato
ocorreu nos anos subsequentes. Uma parte da história já contei ao Prof.
Sérgio Amadeu no
[episódio 92 do podcast Tecnopolítica](https://www.youtube.com/watch?v=gcJ7RnbMjE8).
É fato indiscutível que, nesses anos, ampliaram-se sobremaneira as
situações que nos obrigam, contra a nossa vontade, a aceitar o que quer
que as "*Big Tech*" desejem nos impor.

<figure markdown="1">
![Imagem de celular sobre a mesa com aplicativo aberto.]({{ 'assets/images/2025/04/lana-codes-peHEZs9wFyM-unsplash.jpg' | relative_url }})
<figcaption>Aplicativos que não são subsidiados pelo oligopólio gastam a franquia de internet. Imagem: Lana Codes / Unsplash</figcaption>
</figure>

O pior tipo de armadilha, no entanto, é quando o próprio Estado
estabelece obrigações, ou impõe condições para o recebimento de direitos,
a não ser que o cidadão utilize determinado aplicativo ou rede social das
"*Big Tech*". Hoje vivemos a trágica situação em que todos os aplicativos
governamentais são de código fechado, isto é, não se pode inspecionar o
código fonte para verificar o que de fato estão fazendo e que dados estão
coletando no seu dispositivo.
[Carteira de Identidade Nacional – CIN](https://www.gov.br/governodigital/pt-br/identidade/identificacao-do-cidadao-e-carteira-de-identidade-nacional),
[Carteira Digital de Trânsito – CDT](https://www.gov.br/pt-br/apps/carteira-digital-de-transito-1)
(anteriormente chamada de CNH Digital) e o
[e-Título](https://www.justicaeleitoral.jus.br/titulo-eleitoral/) são
apenas alguns dos exemplos de aplicativos governamentais, produzidos
usando recursos públicos do erário, mas cujo código fonte não é acessível
ao público que pagou por eles. Para saber mais sobre por que o público
deveria ter direito de acesso e uso ao código fonte do software pelo qual
pagou, conheça a campanha
[*Public Money, Public Code*](https://publiccode.eu/pt/) da
[*Free Software Foundation Europe* – FSFE](https://fsfe.org/index.pt.html). Em
contraste com o Brasil, muitos aplicativos governamentais em países da
União Europeia, como a Alemanha, são de código aberto.

A falta de acesso ao código fonte não é o único problema desses
aplicativos governamentais. Talvez seja ainda mais grave o fato desses
aplicativos só serem disponibilizados nas lojas proprietárias da Google e
da Apple. Além da questão da coleta de dados de todos os cidadãos
brasileiros por essas empresas estrangeiras, o que é grave, há ainda
problemas de ordem jurídica e um problema de ordem democrática.
Legalmente, não se pode estabelecer um contrato sob coerção ou ameaça.
Tal contrato não tem validade jurídica. Além disso, o fato de que o
cidadão não pode opinar ou influenciar sobre os termos de serviço e
políticas de privacidade se torna um problema de ordem democrática quando
todos passam ser obrigados pelo Estado a aceitá-los.

O que o Estado está fazendo, com essa prática, é privatizar a lei em um
processo antidemocrático. O cidadão tem que obedecer e não tem nenhuma
participação na definição do texto que supostamente é obrigado a
obedecer. Quem determina o que aparece nesses termos de serviço e
políticas de privacidade são exclusivamente a própria Alphabet, dona da
Google, e a Apple. O que elas escrevem tem força de lei e não há nada que
o cidadão possa fazer, uma vez que o Estado condiciona o cumprimento de
deveres e o acesso a direitos à aceitação desses termos. É uma tirania
das *Big Tech*, com o aval dos governos de países que adotam a prática de
estabelecerem aplicativos de código fechado em lojas proprietárias de
oligopólios estrangeiros como único meio de exercer a cidadania.

Em outros tempos, a tirania levaria à revolta popular contra o tirano. No
caso presente, isso não ocorre, em grande parte, porque as pessoas foram
condicionadas durante anos por essas empresas do oligopólio do Vale do
Silício, a aceitar sem ler e nem prestar atenção às obrigações e
permissões "assentidas" nos termos de serviço. Com isso, conseguiram criar
um sentimento de resignação, em que as pessoas acham que tudo está muito
ruim, mas acreditarem não há nada que se possa fazer.

<figure markdown="1">
![Foto de graffiti representando a resistência por meio de punhos cerrados e braços levantados.]({{ 'assets/images/2025/04/jon-tyson-qn6mBa0twDY-unsplash.jpg' | relative_url }})
<figcaption>Imagem: Jon Tyson / Unsplash</figcaption>
</figure>

Isso não é verdade. Há muito, sim que podemos fazer. Não é fácil, mas há
diversas atitudes que podemos tomar. Para começar, cobrar dos políticos e
votar naqueles que se comprometam com políticas públicas que fomentem a
criação da infraestrutura digital nacional. Por exemplo, que defendam a
ideia de que se o software é desenvolvido com recursos públicos, ele
pertence ao público e deve ter o código livre, como defendido pela
campanha *Public Money, Public Code* da FSFE. Cobrar também que valorizem
a proteção dos dados pessoais e a soberania digital, fomentando o
desenvolvimento de uma infraestrutura digital nacional, tanto em termos
de hardware
([nuvem soberana](https://www.nexojornal.com.br/expresso/2024/10/09/o-que-e-nuvem-soberana-e-por-que-o-brasil-quer-ter-uma)),
quanto em termos de software.

Além disso, é necessário desenvolver e reter os talentos formados na
universidades brasileiras, para que os profissionais de tecnologia
permaneçam no Brasil, em vez de irem trabalhar em empresas estrangeiras,
e para que o país tenha o domínio sobre a tecnologia. Para isso, é
necessário que as universidades possuam financiamento adequado para
pesquisa e ensino na área de tecnologia, no sentido contrário dos cortes
que foram feitos nos últimos anos em nome do ajuste fiscal. Criar
incentivos fiscais para que empresas brasileiras do setor se desenvolvam,
compensando o efeito fiscal com maiores impostos para as empresas
estrangeiras que enxergam o país como colônias digitais para a extração
de dados.

Por outro lado, além das questões relacionadas a políticas públicas,
podemos também tomar diversas atitudes no âmbito pessoal. Usar lojas de
aplicativos livres, como a [F-Droid](https://f-droid.org/) nos
dispositivos móveis baseados em Android. Remover os aplicativos
proprietários e que coletam seus dados, inclusive os que já vêm
instalados no sistema desde a fábrica – os chamados
"*[bloatware](https://pt.wikipedia.org/wiki/Bloatware)*".
Existem guias e tutoriais na internet que demonstram passo a passo como
fazer isso. O fórum [xdaforums.com](https://xdaforums.com/) costuma ter
guias personalizados para cada modelo de dispositivo móvel.

<figure markdown="1">
![Foto de braço com luva segurando produto de limpeza.]({{ 'assets/images/2025/04/jeshoots-com-__ZMnefoI3k-unsplash.jpg' | relative_url }})
<figcaption>Imagem: JESHOOTS.COM / Unsplash</figcaption>
</figure>

Toda vez que for se cadastrar em um novo serviço, avalie cuidadosamente
quais dados pessoais estão sendo pedidos. Eu, como todo mundo, não tenho
tempo para ler em mínimos detalhes todos os termos de serviço de todas as
plataformas, sites, serviços e aplicativos que preciso usar. Por isso, é
importante pesquisar nome do serviço, plataforma ou aplicativo no
[ToS;DR](https://tosdr.org), ver qual é a sua nota de privacidade e os
principais pontos negativos (ou positivos) do resumo dos seus termos de
serviço. Para entender o que é e como usar a ferramenta, leia
[o texto que escrevi sobre o assunto]({{ reference_post.url | relative_url }}).

No âmbito social e nas relações comerciais, preferir sempre
os aplicativos livres para troca de mensagens, navegação com mapas e
outras necessidades do dia a dia. Apresentar às pessoas que conhece os
aplicativos e soluções utilizadas, para que vejam que não só elas reduzem
a nossa exposição de dados pessoais e submissão às empresas do oligopólio
estrangeiro das "*Big Tech*". Tão importante quanto isso é mostrar que
essas soluções também são viáveis, convenientes e fáceis de usar no dia a
dia.
