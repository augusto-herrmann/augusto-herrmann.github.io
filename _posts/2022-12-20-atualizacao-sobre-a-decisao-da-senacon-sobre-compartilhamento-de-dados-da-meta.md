---
layout: post
title: Atualização sobre a decisão da Senacon sobre compartilhamento de dados da Meta
author: Augusto Herrmann
lang: pt
ref: 2022-12-20-update-on-senacons-decision-on-metas-data-sharing
category: [pt, blog]
tags: [whatsapp, meta, privacy, antitrust]
cover: /assets/images/2022/12/ante-hamersmit-U3AKT6ryvic-unsplash.jpg
snippet-image: /assets/images/2022/12/ante-hamersmit-U3AKT6ryvic-unsplash.jpg
desc: >-
  Graças a um pedido pela LAI da Fiquem Sabendo, uma agência focada em
  jornalismo de dados, conhecemos algumas das justificativas por trás
  da decisão da Senacon de arquivar as queixas de organizações da
  sociedade civil quanto às mudanças na política de privacidade do
  WhatsApp e suas práticas de compartilhamento de dados.
image-credits: Ante Hamersmit on Unsplash
---

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2022-11-25-senacon-sees-no-problem-in-whatsapp-data-sharing" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

Há quase um mês eu escrevi sobre como a [Senacon, a Secretaria Nacional
de Defesa do Consumidor, não viu problema nas novas práticas de
compartilhamento de dados do WhatsApp anunciadas pela Meta no ano
passado]({{ reference_post.url | relative_url }}).

Agora, graças a uma solicitação pela Lei de Acesso à Informação feita
pela agência focada em jornalistmo de dados chamada
[Fiquem Sabendo](https://fiquemsabendo.com.br/), podemos saber mais sobre
as justificativas por trás da decisão. Como resposta, eles obtiveram
acesso à
[Nota Técnica n.º 42/2022/CGCTSA/DPDC/SENACON/MJ](/assets/documents/2022/12/Anexo_MJ___20929036___Nota_Tecnica%20da%20Senacon.pdf),
que trata da

> Averiguação Preliminar por supostas violações ao direito do consumidor
> relacionados ao compartilhamento de dados pessoais do WhatsApp para
> grupo de empresas Facebook Inc em violação ao Marco Civil da Internet
> e Código de Defesa do Consumidor. Solicitação de Esclarecimentos por
> este Departamento de Proteção e Defesa do Consumidor. Informações
> Prestadas pela averiguada. Ausência de violação à legislação
> consumerista. Sugestão de Arquivamento.

As principais justificativas alegadas para indeferir a queixa são:

1. o WhatsApp já oferecia uma escolha de "*opt-out*" para os consumidores
   que escolhessem não compartilhar seus dados com o grupo Meta;
2. a empresa alega que as mensagens pessoais são criptografadas de
   ponta a ponta para todos os usuários do WhatsApp, inclusive para
   aqueles que recusaram a opção em 2016;
3. a falta de evidências no processo de vazamentos de dados por parte do
   WhatsApp/Facebook;
4. uma reclamação similar também teria sido rejeitada pela Autoridade
   Nacional de Proteção de Dados -- ANPD, que supostamente não teria
   encontrado violação de privacidade na nova política de privacidade e
   a teria considerado adequada à Lei Geral de Proteção de Dados – LGPD,
   segundo a Nota Técnica n.º 49/2022/CGF/ANPD.

A seguir, vamos explorar por que nenhuma dessas justificativas para de
pé.

## N.º 1: o suposto *Opt-out* e o beco sem saída do WhatsApp

É verdade que o WhatsApp já ofereceu uma opção de *opt-out* para usuários
que não quisessem que seus dados fossem compartilhados com as outras
empresas. Entretanto, a última vez que isso aconteceu foi em 2016 e a
opção não foi mais disponibilizada desde então. Como
[reportado pelo G1](https://g1.globo.com/economia/tecnologia/noticia/2021/01/06/whatsapp-comeca-a-avisar-que-ira-compartilhar-dados-dos-usuarios-com-o-facebook.ghtml):

> A última vez que o app fez uma grande mudança de política de
> privacidade foi em 2016, mas as pessoas que já usavam o app podiam
> negar o compartilhamento de dados com o Facebook. Novas contas, por
> outro lado, não tinham essa opção.

Isso significa que a qualquer um que tenha começado a usar o WhatsApp
depois daquele dia nunca foi ofertada a opção de não compartilhar os
seus dados. Para a Senacon, então, essas pessoas não importam?

Talvez se possa argumentar que elas não deveriam aceitar os termos e
usar o WhatsApp para começo de conversa. Existem aplicativos de mensagem
seguros e em software livre que não são propriedade de gigantes da
tecnologia. Eu mesmo recomendo que se usem eles: como escrevi no último
artigo, o [Element](https://element.io/) e o [Signal](https://signal.org)
são excelentes aplicativos.

Mas o quão prático é isso, dado que praticamente toda relação social e
comercial nesse país é mediada pelo WhatsApp? Se você quiser usar o
Element ou o Signal, você pode tentar convencer a sua família, seus
amigos e colegas a usá-lo também e alguns deles podem até mesmo
experimentar. Mas boa sorte ao tentar pedir alguma coisa na padaria ou
farmácia perto de casa, ou chamar um encanador quando precisar do
serviço. Algumas empresas com as quais você precisa se relacionar muitas
vezes não têm nem mesmo e-mail, mas certamente oferecem serviço de
atendimento ao consumidor pelo WhatsApp. Até mesmo alguns serviços
governamentais são ofertados lá. Há mesmo uma escolha, na prática, para
uma pessoa brasileira **negar** os termos de serviço e não uar o
serviço?

## N.º 2: criptografia de ponta a ponta do quê?

Claro que a Meta alega que o conteúdo das mensagens é criptografado de
ponta a ponta. Acredite ou não nessa alegação. Como o aplicativo é de
código fechado, é completamente impossível verificar a veracidade dessa
alegação.

Ainda assim, mesmo que seja verdade, somente o **conteúdo** das mensagens
é criptografado e a Meta não pode acessá-lo. Os metadados, tais como com
quem você fala, seus números de contato, quando e com que frequência
vocês trocam mensagens entre si, etc., ainda são perfeitamente visíveis
para a Meta e eles de fato os querem a ponto de exigir que você os
compartilhe com os seus parentes corporativos. Para empresas como o
Facebook, que têm na publicidade microdirecionada o seu modelo de
negócios, tais dados têm valor inestimável.

Como aprendemos com cada especialista em segurança, os metadados são tão
ou mais importantes para a nossa privacidade quanto os próprios dados.
Então a desculpa de que a empresa não tem acesso ao conteúdo das
mensagens não tem **nada** a ver com a questão em pauta e não é um
argumento pelo qual indeferir a reclamação.

## N.º 3: se isso não for jogado na minha cara, isso não existe

O terceiro argumento é que o processo não apresenta nenhuma evidência de
vazamentos de dados por parte da Meta. Eu nem preciso gastar muito
esforço para explicar que isso só pode ser considerado uma ignorância
voluntária. Qualquer um que tenha acompanhado as notícias ou faça uma
busca na web descobrirá rapidamente a respeito do
[escândalo de dados Facebook-Cambridge Analytica](https://pt.wikipedia.org/wiki/Esc%C3%A2ndalo_de_dados_Facebook%E2%80%93Cambridge_Analytica)
revelado em 2018, que levou Mark Zuckerberg a ter que depor no Congresso
dos Estados Unidos da América, ou do
[vazamento de dados de meio bilhão de usuários do Facebook em abril de 2021](https://www.wired.com/story/facebook-data-leak-500-million-users-phone-numbers/).

## N.º 4: vamos alegar que outro relatório diz o que ele não diz

Agora isso é interesante. O fato de que outro processo contra a Meta já
tinha sido concluído este ano pela ANPD não era conhecido por mim e não
recebeu tanta atenção da mídia quanto quando a controvérsia começou em
2021.

O site da ANPD tem até mesmo uma
[matéria](https://www.gov.br/anpd/pt-br/assuntos/noticias/anpd-conclui-a-analise-de-adequacao-da-nova-politica-de-privacidade-do-aplicativo-a-lgpd)
explicando o processo e mostra uma linha do tempo semelhante a um
infográfico, mostrando os eventos começando com a mudança dos termos de
serviço em janeiro de 2021.

<figure markdown="1">
![O infográfico da ANPD com a linha do tempo dos eventos no caso do compartilhamento de daods do WhatsApp.]({{ 'assets/images/2022/12/infografico-de-linha-do-tempo-caso-whatsapp.png' | relative_url }})
<figcaption>O infográfico da ANPD com a linha do tempo dos eventos no caso do compartilhamento de daods do WhatsApp.</figcaption>
</figure>

Além disso, eles até disponibilizaram o conteúdo da recomendação conjunta
e três notas técnicas exaradas pela ANPD sobre esse caso:

* [Ato de Recomendação Conjunta (ANPD, Cade, MPF e Senacon)](https://www.gov.br/anpd/pt-br/assuntos/noticias/AtodeRecomendaoConjunta.pdf)
* [Nota Técnica n.º 02/2021/CGTP/ANPD](https://www.gov.br/anpd/pt-br/assuntos/noticias/inclusao-de-arquivos-para-link-nas-noticias/NotaTecnicaANPDWhatsapp_ocr.pdf)
* [Nota Técnica n.º 19/2021/CGF/ANPD](https://www.gov.br/anpd/pt-br/assuntos/noticias/NotaTcnica19.2021.CGF.ANPD.pdf)
* [Nota Técnica n.º 49/2022/CGF/ANPD](https://www.gov.br/anpd/pt-br/documentos-e-publicacoes/nt_49_2022_cfg_anpd_versao_publica.pdf)

Eu ainda não li todas por completo e a análise desses documentos talvez
mereça um artigo dedicado. Eu já posso dizer que a última nota técnica
reconheceu que a Meta atendeu às determinações da autoridade, mas ainda
determinou a instauração de um novo procedimento específico para avaliar
a adequação à LGPD das práticas de compartilhamento de dados da empresa. 

> 7.1.4. Instaure-se procedimento específico para avaliar o
> compartilhamento de dados pessoais entre WhatsApp e as empresas do
> grupo Facebook (Meta), no intuito de apurar sua adequação aos termos
> da LGPD.

Então é completamente falsa a afirmação da Senacon de que a ANPD já
teria julgado as práticas da empresa como adequadas à LGPD:

> 2.4. Constata-se também que as mais recentes atualizações dos Termos
> de Serviço e da Política de Privacidade foram objeto de análise pela
> ANPD, que, após analisar as versões da Política de Privacidade de
> todas as ferramentas do aplicativo WhatsApp (WhatsApp Messenger,
> WhatsApp for Business e WhatsApp for Business - API), concluiu pela
> sua adequação à LGPD, por meio da 3ª Nota Técnica de nº
> 49/2022/CGF/ANPD, expedida em 06 de maio de 2022.

Além do mais, a ANPD tem levado em consideração apenas a adequação à
LGPD, que é a matéria de sua competência. A Senacon, por outro lado
deveria supostamente verificar a adequação à legislação e às normas de
proteção ao consumidor -- um assunto completamente distinto -- e a nota
técnica da Senacon não tem qualquer consideração sobre a questão. De
fato, ela nem mesmo cita quaisquer normas de proteção ao consumidor,
exceto pela citação da própria reclamação no primeiro parágrafo. O fato
de que a ANPD reconheceu que a Meta cumpriu com as suas determinações em
relação aos termos de serviço do WhatsApp é um *non sequitur* para a
conclusão da Senacon.

## Há uma saída?

No fim das contas, ainda continuamos com o problema de uma sociedade
tomada como refém pela Meta. As poucas ocasiões em que milhões de
pessoas de fato decidiram instalar um outro aplicativo de mensagem foram
aquelas em que o judiciário, de maneira inconsequente, o bloqueou em
todo o país em retaliação à noção equivocada de que poderia ser possível
para a empresa entregar o conteúdo de mensagens, criptografas de ponta a
ponta, trocadas entre criminosos. Se esses juízes tivessem assessoria
técnica, poderiam ter pedido ao WhatsApp que entregasse os metadados em
vez disso -- o que possivelmente poderia ter sido suficiente, quando
combinado com outras maneiras de obtenção de provas, para indiciar
qualquer criminoso.

Durante esses blecautes do WhatsApp, milhões de brasileiras e brasileiros
instalaram o Telegram e outros aplicativos de mensagens. Mas assim que o
WhatsApp voltou a ficar disponível, essas pessoas desinstalaram esses
aplicativos e voltaram a usar aquilo que estavam acostumadas -- o
WhatsApp.

Também vale mencionar mais uma vez que a absoluta dominância do WhatsApp
no mercado brasileiro é [consequência da prática de *zero rating*, ou
franquia zero](https://www.youtube.com/watch?v=gcJ7RnbMjE8) -- na qual a
empresa abusa do seu poder econômico ao subornar as empresas de internet
móvel para manter os seus aplicativos fora dos limites estritos de
tráfego de dados (franquia de dados) que são o seu modelo de negócios. E
contam com a complacência de entidades governamentais como o Cade e a
Anatel, que desde 2018 institucionalizaram o zero rating ao arrepio da
neutralidade da rede determinada pelo
[Marco Civil da Internet](https://pt.wikipedia.org/wiki/Marco_Civil_da_Internet).

Se o WhatsApp tivesse sido bloqueado dessa vez por uma razão que fosse
de fato justificável, talvez poderia ter sido o empurrãozinho para que
os efeitos de rede, combinados com o fogo de palha que foi a consciência
do público momentânea sobre as práticas questionáveis de
compartilhamento de metadados usadas por muitas empress, funcionassem
para criar alguma concorrência e diversidade de fato no cenário dos
aplicativos de mensagens.
