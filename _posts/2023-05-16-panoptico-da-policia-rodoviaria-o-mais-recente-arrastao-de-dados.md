---
layout: post
title: "Panóptico da polícia rodoviária: o mais recente arrastão de dados"
author: Augusto Herrmann
lang: pt
ref: 2023-05-16-road-police-panopticon-the-latest-data-grab
category: [pt, blog]
tags: [vigilância em massa, privacidade, rastreamento de veículos, biometria, cnh, siniav]
cover: /assets/images/2022/12/alberto-rodriguez-santana-i_nIoSCdHv4-unsplash.jpg
snippet-image: /assets/images/2022/12/alberto-rodriguez-santana-i_nIoSCdHv4-unsplash.jpg
desc: >-
  A Polícia Rodoviária Federal tem acumulado dados em instrumentos de
  vigilância em massa. O seu último arrastão de dados é uma proposta para
  construir um banco de dados para rastrear e guardar para sempre quase
  todos os movimentos de todos os veículos no país.
image-credits: Alberto Rodríguez Santana on Unsplash
---

A Polícia Rodoviária Federal (PRF), logo depois de ter sido denunciada
pelo veículo de imprensa The Intercept por adquirir dados biométricos de
todos os motoristas brasileiros no mês passado
([mais informações sobre isso adiante](#biometric-data-another-recent-personal-data-grab-by-prf)),
ataca novamente com uma nova medida de vigilância em massa: identificar e
armazenar a passagem de cada veículo em 1.921 pontos de verificação com
sensoriamento remoto por câmeras, usando o reconhecimento de placas
veiculares. O processo está passando por uma
[consulta pública](https://www.gov.br/participamaisbrasil/cp-prf-2023-monitoramentoeletronico)
relâmpago, que acabou de abrir na última quinta-feira, 11 de maio, e já
está terminando hoje. Um prazo tão curto dá à sociedade civil quase
nenhum tempo para analisar a proposta ou para organizar qualquer tipo de
mobilização contra ela.

## Um histórico de vigilância em massa de movimentação de veículos

Sucessivos governos no Brasil têm insistido na ideia de que o histórico
de movimentos de todos os veículos deveriam ser rastreados, coletados e
armazenados eternamente em um banco de dados.

### Siniav: um chip RF de identificação obrigatória para todos os veículos

O Conselho Nacional de Trânsito (Contran) estabeleceu uma norma
([Resolução n.º 412](https://www.gov.br/infraestrutura/pt-br/assuntos/transito/conteudo-contran/resolucoes/resolucao4122012.pdf))
em 2012 que criou o Sistema Nacional de Identificação Automática Veicular
– *Siniav*. O sistema tornava obrigatória a instalação de chips de
radiofrequência (RF) em todos os veículos e era para ser implementado de
maneira gradual. Antenas instaladas em diversos pontos de circulação
leriam as informações no chip, que identificaria unicamente o veículo e
poderia gravar a hora e a posição em que ele passou.

O motivo alegado para a medida foi para facilitar o combate ao furto e
roubo de veículos e cargas. Na prática, ele possibilitaria criar um
banco de dados contendo o histórico completo de movimentação de cada
veículo. Tal base de dados estaria então sujeita a diversos tipos de
abusos e vazamentos de dados.

Conforme [explicado](https://www.oabsp.org.br/noticias/2007/10/16/4475/)
por Marcos da Costa, advogado da OAB de São Paulo:

> No caso do chip para os carros, as autoridades estaduais e municipais
> confirmam que pode armazenar o número de série do veículo, placa,
> chassi e código Renavan, e tem capacidade de mapear o trajeto realizado
> por cada veículo. Preocupa-nos, neste primeiro momento, a captura e
> armazenamento de dados podendo expor a privacidade das pessoas.
> Armazenados esses dados, podem eles sozinhos, ou somados a outras
> informações, vir a sofrer tratamento automatizado, com resultados
> devastadores para a privacidade do motorista.

Após sucessivos adiamentos dos prazos de implementação, o chip de
rastreamento obrigatório, juntamente com um igualmente problemático chip
SIM com rastreamento por GPS chamado *Simrav*,
[foram suspensos pelo Tribunal Regional Federal da 3ª Região](https://g1.globo.com/carros/noticia/2015/04/ameaca-privacidade-barrou-outro-projeto-de-chip-em-carro.html)
depois de uma ação movida pelo Ministério Público Federal no Estado de
São Paulo.

> "Rastrear e localizar indicam a mesma coisa, pois ambos referem-se à
> possibilidade de encontrar o veículo - e por conseguinte seu condutor -
> aonde quer que esteja" — Cecília Marcondes, desembargadora federal

No ano seguinte, em 2015, o Contran
[decidiu suspender a obrigação de instalar os chips RF](https://g1.globo.com/carros/noticia/2015/10/contran-suspende-obrigatoriedade-de-chip-com-rastreador-em-veiculos.html).

### Siniav: o retorno do chip RF dentro da placa veicular

Mais recentemente, no entanto, o Contran encontrou uma nova maneira de
forçar a identificação por chip RF aos brasileiros. Um acordo internacional
entre os países do Mercosul em 2014 estabeleceu
[um modelo comum para placas](https://pt.wikipedia.org/wiki/Placas_de_identifica%C3%A7%C3%A3o_de_ve%C3%ADculos_no_Mercosul)
para todos os veículos nesses países. Esse modelo de placa veicular tem
sido gradualmente implantado desde 2018 e é obrigatório para todos os
veículos novos vendidos desde 2020.

O Contran publicou outra norma estabelecendo que essas novas placas
veiculares devem vir com um chip RF identificador dentro de si.
[Segundo o Denatran](https://www.portaldotransito.com.br/noticias/denatran-responde-alguns-questionamentos-sobre-as-placas-mercosul-2/),

> *22. O chip conseguirá fazer rastreamento do veículo?*
> 
> O chip não fará o rastreamento, apenas o controle de passagem dos
> veículos nos locais de instalação das antenas. O chip não conterá
> informações sobre o veículo nem tampouco do proprietário, apenas
> conterá um número de identificação criptografado para ser utilizado
> pelas instituições que tiverem a autorização do DENATRAN. O número de
> identificação será a chave de acesso aos dados cadastrais autorizados,
> conforme cada aplicação da instituição que solicite o serviço.

Se as instituições autorizadas (presume-se que, pelo menos, os Detrans
locais serão autorizados) podem decodificar e ler esse número de
identificação e então associá-lo univocamente ao resto dos dados nas suas
próprias bases de dados e na base de dados do Denatran, inclusive a
informação do seu proprietário, eles serão obviamente capazes de guardar
em seus bancos de dados a posição, o registro de tempo e a identificação
única do veículo (Renavam). Assim, para obter o histórico completo de todos
os momentos em que cada veículo, ou o seu proprietário, já passou por
cada antena, basta fazer uma consulta SQL. Em todo caso, o instrumento
de vigilância em massa sem autorização judicial e o regime de violação
de privacidade ainda é o mesmo.

### Córtex: ubiquidade nas referências cruzadas de dados pessoais

Como evidenciado no argumento acima, quando dados pessoais são combinados
e referenciados em diferentes bases de dados, o potencial para danos é
multiplicado.

Em 2020 o Ministério da Justiça foi
[denunciado pelo The Intercept por implementar o Córtex](https://www.intercept.com.br/2020/09/21/governo-vigilancia-cortex/),
um sistema capaz de associar dados pessoais de cidadãos brasileiros a
partir de muitas bases de dados governamentais. De acordo com a matéria,
o sistema era operado na época pela Secretaria de Operações Integradas –
Seopi. Eles mostram em um vídeo que pode-se começar pelo CNPJ de uma
empresa, localizar um empregado em particular dentro da lista de todos os
seus empregados, junto com as datas de nascimento e CPFs. Então, se o
empregado possui um carro, eles podem ver o itinerário inteiro de quando
e por onde eles têm dirigido, tudo sem obter mandado judicial.

Isso demonstra como o processo de coleta de pontos de dados identificando
todos os veículos, registros de tempo e localizações de antenas
constituem, de fato, um sistema de vigilância em massa.

## Dados biométricos: outro arrastão de dados recente da PRF

No mês passado a PRF apareceu no noticiário por
[estabelecer um contrato para obter do Denatran dados biométricos de todos os motoristas brasileiros](https://www.intercept.com.br/2023/05/02/prf-desrespeita-lei-e-compra-copia-da-base-de-dados-biometricos-de-todos-os-motoristas-com-cnh-no-brasil/),
algo que especialistas sustentam que mal poderia ser justificado.

> “Não há uma justificativa clara do porque precisam desse enorme banco
> de dados. E isso impossibilita até fazer previsões sobre as
> finalidades, porque são inúmeras”, explica o pesquisador Felipe Rocha,
> do Laboratório de Políticas Públicas e Internet, o Lapin, que integra o
> Comitê Central de Segurança de Dados, criado em 2019, para gerenciar o
> compartilhamento de informações pessoais com o governo.

Os dados biométricos incluem fotografias de alta resolução e as
impressões digitais dos dez dedos de cada motorista, um banco de dados
do Departamento Nacional de Trânsito (Denatran).

Essa base de dados em si pode violar o princípio da necessidade
estabelecido pela Lei Geral de Proteção de Dados (LGPD), conforme
dispõe o artigo 6:

> III – necessidade: limitação do tratamento ao mínimo necessário para a
> realização de suas finalidades, com abrangência dos dados pertinentes,
> proporcionais e não excessivos em relação às finalidades do tratamento
> de dados;

Isto é, se a finalidade é identificar o motorista, se isso pode ser
realizado usando somente a fotografia, por que tomar as impressões
digitais? Mesmo se alguém pudesse defender a coleta de digitais, o que
poderia ser feito com todas as dez digitais que não pudesse ser feito
com apenas uma única digital?

É claro, o mesmo argumento também vale para a base de dados do Tribunal
Superior Eleitoral (TSE), que é usada nas eleições brasileiras e contém
os exatos mesmos tipos de dados biométricos, porém de todos os cidadãos,
e não somente aqueles com Carteira Nacional de Habilitação (CNH).

Por sua vez, o compartilhamento de dados entre o Denatran e a PRF em si
pode também violar o primeiro princípio, o da finalidade da coleta e do
processamento de dados pessoais:

> I – finalidade: realização do tratamento para propósitos legítimos,
> específicos, explícitos e informados ao titular, sem possibilidade de
> tratamento posterior de forma incompatível com essas finalidades;

Vale mencionar que, ao contrário de senhas, as pessoas não podem mudar os
seus dados biométricos, uma vez vazados. Então bancos de dados como esses
sempre carregam um risco imenso de causar danos irreparáveis a todos, a
tal ponto que precisamos nos questionar se faz sentido que elas sequer
existam para início de conversa.

## Instrumentalização política com uso de dados pela PRF

Com tantos dados pessoais em mãos vem ainda mais poder. Quando esse poder
é abusado ou um vazamento de dados ocorre, o dano realizado aumenta em
proporção com a quantidade ou a sensibilidade dos dados pessoais.

Em outubro de 2022 a PRF foi denunciada na imprensa por deflagrar uma
operação especial para parar veículos, em especial ônibus, e impedi-los
de seguir viagem em caso de qualquer possível irregularidade. Essas
operações foram especialmente concentradas em locais da região nordeste
onde houve maior concentração de eleitores do então candidato, agora
presidente, Lula, no primeiro turno. Como o então presidente Bolsonaro
proferia abertamente que interferiria em organizações públicas em favor
próprio, a operação foi percebida por muitos como um abuso de poder para
interferir ilegalmente nas eleições.
[Evidências encontradas no mês passado pela Polícia Federal com o ex-Ministro da Justiça](https://g1.globo.com/politica/blog/andreia-sadi/post/2023/04/28/pf-recebe-mapeamento-usado-por-anderson-torres-para-operacao-no-2o-turno-das-eleicoes.ghtml)
de fato corroboram essas suspeitas. As investigações sobre o caso ainda
estão em curso.

## Conclusão

Deve restar claro até aqui que coletar e armazenar a identificação de
todos os veículos que passam por um ponto de leitura, por quaisquer meios,
sejam eles o reconhecimento ótico de caracteres nas placas veiculares ou
chips RF, levará a bases de dados que armazenam todos os movimentos dos
cidadãos para sempre. Ferramentas que possibilitam a vigilância em massa
de todos sem escrutínio judicial, sem obter um mandado, são uma violação
do
[direito constitucional à proteção de dados](https://www.gov.br/anpd/pt-br/protecao-de-dados-pessoais-agora-e-um-direito-fundamental)
e devem ser rejeitadas e revogadas.
