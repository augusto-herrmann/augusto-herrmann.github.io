---
layout: post
title: "Tokens e atribulações"
lang: pt
ref: 2019-06-12-tokens-and-atribulations
cover: /assets/images/2019/06/brina-blum-156977-unsplash.jpg
tags: [certificado digital, ICP Brasil, token criptográfico]
---

Após quinze anos acompanhando de longe a evolução da Infraestrutura de Chaves
Públicas Brasileira – ICP Brasil, enfim, adquiri um certificado próprio. E, com
ele, um token em hardware para armazenar a chave privada. Decidi, então tentar
instalá-lo e operá-lo em um sistema operacional Ubuntu 18.04.2 LTS e documentar
os passos para ajudar outras pessoas que porventura queiram utilizá-lo no mesmo
sistema e encontrem dificuldades.

# Instalando o token usb para certificado digital

Para instalar os drivers do token GD Starsign da Giesecke & Devrient GmbH no
Ubuntu 18.04.2 LTS, baixe os drivers a partir da
[página de drivers da GD América do Sul](http://safesign.gdamericadosul.com.br/projeto_safesign/)
e descompacte os arquivos.
Apesar do nome dos drivers serem para dispositivos "Safesign", eles são
compatíveis com o modelo do tipo "Starsign".

Instale as dependências do pacote com o comando:

```
$ sudo apt install libccid pcscd libpcsclite1
```

## O pacote que falta

Os drivers possuem uma dependência adicional que não está disponível no Ubuntu
18.04 LTS: o pacote `libgdbm3`. Todavia, se você tentar instalá-lo, acontecerá
o seguinte:

```
$ sudo apt install libgdbm3
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
O pacote libgdbm3 não está disponível, mas é referenciado por outro pacote.
Isto pode significar que o pacote está faltando, ficou obsoleto ou
está disponível somente a partir de outra fonte

E: O pacote 'libgdbm3' não tem candidato para instalação
```

Isto porque esse pacote não está disponível no Ubuntu 18.04 LTS "Bionic
Beaver". Entretanto, estava disponível na versão LTS anterior,
o 16.04 Xenial, que
[tem a versão 1.8.3-13.1 da libgdbm3](https://packages.ubuntu.com/xenial/libgdbm3),
e também no Debian 9 (Stretch), que
[tem a versão 1.8.3-14](https://debian.pkgs.org/9/debian-main-amd64/libgdbm3_1.8.3-14_amd64.deb.html)
desse pacote. Como o Ubuntu é baseado no Debian, o pacote do Debian funciona
também no Ubuntu. É uma escolha pessoal qual deles instalar. Como o Debian tem
a versão mais recente, acbaei optando por ela.

Para instalar o pacote, basta fazer o download no respectivo link e executar
o comando:

```
$ sudo dpkg -i libgdbm3_1.8.3-14_amd64.deb
A seleccionar pacote anteriormente não seleccionado libgdbm3:amd64.
(Lendo banco de dados ... 293686 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar libgdbm3_1.8.3-14_amd64.deb ...
A descompactar libgdbm3:amd64 (1.8.3-14) ...
Configurando libgdbm3:amd64 (1.8.3-14) ...
A processar 'triggers' para libc-bin (2.27-3ubuntu1) ...
```

## Segurança

O problema da abordagem de se instalar pacotes individuais como esse é que,
por não ser gerenciado pelo `apt` ou outro gerenciador de pacotes, se for
descoberta uma vulnerabilidade no mesmo, a correção não será automaticamente
atualizada. Dificilmente o usuário vai atualizar o pacote manualmente, pois
isso não é prático.

Como estamos falando de um token USB para usar um certificado digital para
assinar documentos com validade jurídica, esse problema se torna ainda mais
crítico. Só nos resta esperar que, no futuro, a Giesecke & Devrient GmbH
venha a fornecer um driver que não possua uma dependência não-gerenciada,
como é hoje.

Em contato com representante da
[G+D Mobile Security](https://www.gi-de.com/en/br/mobile-security/),
representante da Giesecke & Devrient GmbH, ao questionar sobre o problema,
fui informado de que seria solicitado ao fornecedor uma posição sobre os
drivers atualizados. Se eu receber uma resposta mais conclusiva no futuro,
atualizarei este post.

## Instalando o driver

Com as dependências solucionadas, é hora de instalar o driver que baixamos
no primeiro passo. Cabem aqui as mesmas observações que fiz sobre a
dependência `libgdbm3`: a instalação do pacote isolado não é gerenciada
para receber atualizações. Melhor seria que a G+D Mobile Security oferecesse
um repositório PPA para Ubuntu, de modo que pelo processo de atualizações do
sistema operacional o driver pudesse ser atualizado.

Na verdade, o ideal mesmo seria que o driver tivesse o seu código aberto e
estivesse disponível diretamente nos repositórios do Debian, Ubuntu, CentOS
e nas distribuições de Linux mais utilizadas. Mas sabemos que muitas empresas
de hardware têm a mentalidade de esconder o código dos seus drivers, com medo
de que os fabricantes concorrentes copiem ou façam engenharia reversa dos
dispositivos.

Para instalar o driver proprietário do GD Starsign, após descompactar o
arquivo baixado, execute:

```
$ sudo dpkg -i SafeSign\ IC\ Standard\ Linux\ 3.5.0.0-AET.000\ ub1604\ x86_64.deb 
A seleccionar pacote anteriormente não seleccionado safesignidentityclient.
(Lendo banco de dados ... 293694 ficheiros e directórios actualmente instalados.)
A preparar para desempacotar SafeSign IC Standard Linux 3.5.0.0-AET.000 ub1604 x86_64.deb ...
A descompactar safesignidentityclient (3.5.0.0-AET.000) ...
Configurando safesignidentityclient (3.5.0.0-AET.000) ...
A processar 'triggers' para libc-bin (2.27-3ubuntu1) ...
A processar 'triggers' para hicolor-icon-theme (0.17-2) ...
A processar 'triggers' para desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
A processar 'triggers' para gnome-menus (3.13.3-11ubuntu1.1) ...
A processar 'triggers' para mime-support (3.60ubuntu1) ...
A processar 'triggers' para bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
A processar 'triggers' para man-db (2.8.3-2ubuntu0.1) ...
```


## Testando o token

Para testar o token, insira-o na porta USB e use o seguinte comando. Caso
apareça o nome do dispositivo, signfica que a instalação foi bem sucedida.

```
$ pcsc_scan 
PC/SC device scanner
V 1.5.2 (c) 2001-2017, Ludovic Rousseau <ludov...@free.fr>
Using reader plug'n play mechanism
Scanning present readers...
0: Giesecke & Devrient GmbH StarSign Crypto USB Token (00000000000000) 00 00
```

## Configurando as aplicações

O próximo passo é configurar o certificado para que funcione nas principais
aplicações em que você pode querer usar assinaturas digitais ou autenticação
de usuário por certificado digital. Vamos ver como fazer isso no
[Firefox](https://support.mozilla.org/en-US/questions/1059377),
[LibreOffice](https://help.libreoffice.org/Common/Applying_Digital_Signatures)
e no [SEI](https://softwarepublico.gov.br/social/sei/sobre-o-sei) (ferramenta
de processo eletrônico muito usada em órgãos públicos.

### Mozilla Firefox

No Firefox (para referência, estamos usando a versão 67), abra o menu sanduíche
e selecione preferências. Alternativamente, pode-se digitar `about:preferences`
na barra de endereços. Selecione o menu "Privacidade e Segurança" na coluna
esquerda. A configuração do token está na última opção, "dispositivos de
segurança.

![Imagem de tela de configurações do Firefox, salientando a opção "dispositivos
de segurança"]({{ 'assets/images/2019/06/firefox-dispositivos-de-seguranca.gif' | relative_url }})

Em seguida, clique o botão "carregar". No campo "nome do módulo", coloque
qualquer descrição que desejar. No exemplo, usamos "Token USB PKCS#11".
Em nome do arquivo do módulo, digite (ou selecione pelo botão "procurar")
o caminho `/usr/lib/libaetpkss.so`. Se o token tiver sido instalado
corretamente nos passos anteriores, esse arquivo do driver deverá estar
presente.

![Imagem da tela de configurações do Firefox, ilustrando a seleção do
arquivo do driver]({{ 'assets/images/2019/06/firefox-token-driver.gif' | relative_url }})

Se tudo deu certo, o gerenciador de dispositivos do Firefox mostrará
o módulo adicionado e todos os dispositivos (tokens) que estiverem
conectados no momento. No caso, selecionamos o token Giesecke & Devrient
GmbH StarSign Crypto USB Token e podemos ver as informações de modelo,
fabricante, rótulo do token, numero de série, etc.

![Imagem de tela de configurações do Firefox, mostrando o token instalado]({{ 'assets/images/2019/06/firefox-token-instalado.gif' | relative_url }})

Agora ele já pode ser utilizado para acessar sites que exigam autenticação
por certificado digital. Por exemplo, se o seu certificado é da Infraestrutura
de Chaves Públicas – [ICP Brasil](http://www.iti.gov.br/icp-brasil), ele pode
ser usado para acessar as suas declarações de imposto de renda no site da
Receita Federal do Brasil.

### LibreOffice

O LibreOffice oferece a possibilidade de assinar digitalmente documentos.
Felizmente, ele é capaz de ler as configurações do Firefox. Então, se você
realizou a configuração do passo anterior, é simples poder utilizar o
certificado digital também no LibreOffice.

Selecione a opção "opções" do menu "ferramentas". Alternativamente, use o
atalho de teclado `ALT+F12`.

![Imagem da tela de configurações do LibreOffice, mostrando onde configurar
o certificado, na seção "segurança".]({{ 'assets/images/2019/06/libreoffice-certificado.png' | relative_url }})

Na seção principal de configurações (a primeira, de nome "LibreOffice"),
escolha "segurança". Na seção "caminho do certificado", clique o botão
"certificado...". Selecione a opção de utilizar o caminho do Firefox e clique
"ok". O LibreOffice pedirá para ser reiniciado. Aceite. Obs.: mesmo clicando
em "reiniciar agora", pelo menos na versão que eu uso (6.0.7.3), ele não se
reinicia. Nesse caso, reinicie manualmente fechando todas as janelas abertas
do LibreOffice (Writer, Calc, Impress, etc.).

A partir de agora, em condições normais os documentos já podem ser assinados.
Antes de assinar, é necessário que um documento esteja salvo. Para testar,
crie e salve um documento para teste ou então abra um documento existente.
Então use o menu "arquivo", "assinaturas digitais", "assinaturas digitais".
Alternativamente, também é possível chegar à mesma tela pelo menu "arquivo",
"propriedades", "geral", "assinaturas digitais". A partir dessa tela, pode-se
assinar clicando o botão "assinar documento", selecionando o certificado a
partir da lista e clicando em "assinar".

#### Exportação do certificado do token

Caso o certificado não apareça na lista, será necessário importar o certificado
manualmente, para que figure entre os certificados reconhecidos pelo sistema
operacional para o seu usuário. Primeiro, exporte o certificado a partir do
token. Insira o token e abra a aplicação "tokenadmin" a partir do Dash do
Gnome. Essa aplicação deve estar presente se o driver do token tiver sido
instalado corretamente. Dentro da aplicação, deve aparecer o token que está
inserido sob "nome da leitora ou do token" e "status do token" como
"operacional". Selecione o token com duplo clique. Sob "objetos do token", deve
aparecer o certificado. Clique em "ver certificado".

![Tela da aplicação tokenadmin, mostrando os objetos do token. Está salientado
o botão "Ver Certificado".]({{ 'assets/images/2019/06/exportar-certificado.gif' | relative_url }})

Clique o o botão "salvar certificado". Escolha um local e um nome para o
arquivo do certificado com a extensão `.cer`.

#### Importação do certificado no seahorse

A exportação do certificado a partir do token está concluída. Agora é hora de
importar o certificado no gerenciador de certificados do sistema operacional.
No Ubuntu, a aplicação padrão que vem instalada para isso é o Seahorse. Pode-se
abri-la, se você ainda está no LibreOffice, a partir do botão "iniciar o
gerenciador de certificados", a partir da tela "assinaturas digitais". Ou
então, diretamente, abra o Seahorse digitando "Seahorse" ou "Senhas e
chaves" a partir do Gnome Dash. Escolha o menu "arquivo", "importar..." e
selecione o arquivo com extensão `.cer`, que foi exportado na etapa anterior.

Serão então mostrado os principais dados do certificado (nome, autoridade
certificadora, data de expiração). Clique o botão importar. A patir de agora,
o certificado deve aparecer entre as opções do LibreOffice

#### Bug no Ubuntu 18.04.2 LTS

Ou deveria. Pelo menos, há relatos de que em outras distribuições de GNU Linux,
ou mesmo na versão 16.04 LTS do Ubuntu, isso funcionava. Mas o bug está
presente [no Ubuntu tanto na versão 18.04 LTS quanto na 19.04](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/1771880),
além de [versões recentes de Manjaro e Fedora](https://gitlab.gnome.org/GNOME/seahorse/issues/205).

O que ocorre é que o botão "importar" fica indisponível. Ao passar o mouse
sobre ele, vem a mensagem "não foi possível importar, pois não há importadores
compatíveis".

![Ilustração do bug no Seahorse 3.20.0. É exibida a mensagem "não foi possível
importar, pois não há importadores compatíveis".]({{ 'assets/images/2019/06/seahorse-bug.gif' | relative_url }})

Aparentemente, o bug no Seahorse vem de uma dependência chamada `libgcr` e
também afeta outras aplicações que o utilizam como o Gnome Keyring. O
[bug](https://gitlab.gnome.org/GNOME/gcr/issues/22) foi reportado na `libgcr`,
mas até o momento não tem uma solução.

Por enquanto, não consegui encontrar uma forma de contornar o problema.
Ainda não há uma maneira de assinar documentos com o certificado digital no
LibreOffice, no Ubuntu 18.04 LTS e 19.04, bem como em boa parte das
distribuições de GNU Linux que usam as mesmas dependências.

### Assinatura de documentos no SEI

O SEI, ou "Sistema Eletrônico de Informações" (o nome mais não descritivo da
história dos softwares, dado que qualquer sistema, em se falando de software,
é eletrônico e lida com informações), é um sistema desenvolvido pelo Tribunal
Regional Federal da 4ª Região – TRF4 para automatizar os processos judiciais,
que até então tramitavam em papel. Embora não seja software livre, e de fato
o tribunal mantém um controle estrito sobre as alterações de código do
software, ao longo dos anos ele tem sido cedido para uso de vários órgãos da
administração pública no Brasil, em todas as esferas, para tornar digitais os
processos administrativos que até então existiam em meio físico, o papel.

Os processos administrativos são cojuntos de documentos oficiais, que muitas
vezes precisam ser assinados pela parte interessada ou pelo autor do ato
oficial, como forma de garantir a sua autoria e autenticidade como
representação da manifestação de intenção do assinante. Na transição para o
meio digital, é necessário encontrar uma forma de estabelecer uma garantia à
assinatura em papel. Foi com esse objetivo que foi criada, em 2001, a
Infraestrutura de Chaves Públicas Brasileira – ICP Brasil, por meio da
[Medida Provisória 2.200-2](https://www.lexml.gov.br/urn/urn:lex:br:federal:medida.provisoria:2001-08-24;2200-2).
Ela estabelece a validade jurídica das assinaturas digitais realizadas com
um certificado da ICP Brasil (art. 1º).

Se você está se perguntando por que uma medida provisória do ano de 2001 está
em vigor até hoje, trata-se de uma medida anterior à alteração constitucional
das regras para a edição de medidas provisórias, trazidas pela
[Emenda Constitucional n.º 32, de 2001](http://www.planalto.gov.br/ccivil_03/Constituicao/Emendas/Emc/emc32.htm).
Ela estabeleceu, no art. 2º, uma regra especial para as medidas provisórias
vigentes à época:

> Art. 2º As medidas provisórias editadas em data anterior à da publicação
> desta emenda continuam em vigor até que medida provisória ulterior as revogue
> explicitamente ou até deliberação definitiva do Congresso Nacional.

Desde então, o Congresso Nacional nunca se mexeu para transformá-la em lei, o
que nos leva a essa situação bizarra de que, em pleno momento de transformação
digital, tanto do setor público quanto do privado, uma parte significativa da
infraestrutura legal para isso está amparada em uma medida provisória que este
ano completará sua "maioridade", fazendo 18 anos, sem se tornar definitiva.

Voltando ao SEI, ele permite aos seus usuários assinar documentos
eletronicamente usando apenas a sua senha de acesso ao sistema, ou usando um
certificado digital. A assinatura usando apenas senha de acesso está amparada
apenas por um decreto e, do ponto de vista da segurança, é algo muito frágil,
uma vez que alguém que realizasse um acesso indevido ao banco de dados do
sistema poderia alterar ou forjar qualquer assinatura. Isso não ocorre com
assinaturas digitais usando um certificado digital, as quais, pelo menos
enquanto os algoritmos de criptografia utilizados forem considerados seguros,
não podem ser forjados. Além disso, esse tipo de assinatura tem o respaldo da
MP 2.200-2, art. 1º, que tem força de lei, para ter validade legal como
uma assinatura.

Então não é difícil perceber qual desses tipos de assinatura suportados pelo
SEI é preferível. Há várias questões de usabilidade, de segurança, de amparo
legal e de gestão de projeto de software, tanto em relação ao SEI quanto em
relação à ICP Brasil que mereceriam ser discutidas em uma postagem em separado.
Mas aqui nos concentramos nas questões práticas de como operar o certificado
digital nesse contexto.

Em tese, tendo o certificado instalado, para usá-lo, bastaria clicar a opção
"assinar", em um documento do SEI, e em seguida selecionar a opção
"certificado digital". Entretanto, ao fazer isso, em uma instância do SEI,
me deparei com uma tela com a mensagem "processando". E assim permanece
indefinidamente. Não sei se é algum problema de configuração na instância do
SEI ou se o suporte do SEI à assinatura com certificado digital é falho. A
certeza é que o certificado está funcionando no navegador, o que pude
verificar em outros sites que permitem o acesso com certificado digital.

![Imagem de tela do SEI, após clicar a opção de assinar com certificado
digital, travada na mensagem "processando".]({{ 'assets/images/2019/06/sei-assinatura-processando.gif' | relative_url }})

À medida em que tiver mais informações sobre as correções desses problemas,
atualizarei esta postagem.

