---
layout: post
title: Como instalar e configurar o CKAN 2.9.0 usando o Docker
author: "Augusto Herrmann"
lang: pt
ref: 2020-09-30-how-to-install-and-configure-ckan-2-9-0-using-docker
category: [pt, blog]
tags: [ckan, docker, tutorial]
cover: /assets/images/2020/09/max-gotts-AFg4iczGE9g-unsplash.jpg
snippet-image: /assets/images/2020/09/ckan-master-class-moscow-urban-forum-2014.jpg
desc: >-
  Depois de alguns anos, tento novamente usar o CKAN com o Docker.
  Vamos descobrir o quão simples (ou não) é subir um catálogo de dados
  abertos com a versão 2.9.0 do CKAN.
image-credits: "Max Gotts / Unsplash"
---

Em 2014, fui convidado a fazer dois minicursos de CKAN, sendo um deles na
agradável ilha de Florianóplis e o outro no inverno congelante de Moscou. Eu
já tinha tido alguma experiência com ele
[quando criamos colaborativamente o portal de dados abertos dados.gov.br](https://dadosabertos.social/t/como-construir-um-portal-de-forma-aberta-e-colaborativa/225)
em 2012, mas eu tive que estudá-lo novamente em 2014 para me atualizar com
os desenvolvimentos então mais recentes.

<figure markdown="1">
![Augusto com um microfone no palco do IV Fórum Urbano de Moscou, apresentando o CKAN]({{ 'assets/images/2020/09/ckan-master-class-moscow-urban-forum-2014.jpg' | relative_url }})
<figcaption>Augusto apresenta o seu curso de CKAN no IV Fórum Urbano de Moscou em
2014 (créditos da foto:
<a target="_blank" href="https://www.flickr.com/photos/mosurbanforum/albums/72157649677233946">Fórum Urbano de Moscou</a>).</figcaption>
</figure>

Os slides desses minicursos, um em inglês e o outro em português, estão
disponíveis no SlideShare:

* [CKAN Overview](https://pt.slideshare.net/AugustoHerrmannBatis/ckan-overview)
  (apresentado no
  [IV Fórum Urbano de Moscou](https://mosurbanforum.com/archive/2014/), em Moscou, em inglês)
* [Minicurso de CKAN](https://pt.slideshare.net/AugustoHerrmannBatis/minicurso-de-ckan)
  (apresentado na conferência
  [Linked Open Data Brasil](https://web.archive.org/web/20180408101700/http://lodbrasil.com.br/)
  em Florianóplis)

Eles se baseiam na versão 2.2 do CKAN e abordam tópicos que vão desde coisas
técnicas, como instalar, configurar e dar manutenção no CKAN até a operação
diária pelos editores e pessoas que irão escrever as descrições dos conjuntos
de dados, preencher os metadados sobre recursos (ex.: o formato de um arquivo),
etc.

Agora, o departamento local de TI está interessado em usar o CKAN e me
perguntou sobre ele, então aproveitei essa oportunidade para mais uma vez
obter uma experiência "mão na massa" ao instalar e configurar a versão atual.
Que, no momento da escrita deste texto, é a 2.9.0.

## O que mudou?

Naquela época, já havia uma maneira de se instalar o CKAN usando uma imagem
Docker, mas era um pouco experimental. Acho que não havia uma receita do
Docker Compose para isso, já que o Docker Compose era muito recente na época.
A maneira mais recomendada de se instalar ainda era a partir do código fonte.
Hoje em dia, os containers Docker são a ordem do dia para manter a sua
infraestrutura de TI bem organizada. Você teria que arrumar uma desculpa muito
boa para não usá-los.

A
[documentação do CKAN ainda oferece três maneiras de se instalar](https://docs.ckan.org/en/2.9/maintaining/installing/index.html),
então isso não mudou. Felizmente, usar o Docker ainda é um caminho possível e
suportado para isso. As opções são:

* pacotes do sistema operacional, disponíveis para Ubuntu 18.04 e 20.04;
* a partir do código fonte, se você tiver um outro sistema operacional ou
  quiser desenvolver o CKAN; ou
* usar o Docker Compose, para uma infraestrutura mais gerenciável, baseada em
  containers.

Como pode estar óbvio a partir do título, vamos usar a instalação baseada em
Docker Compose.

Vamos simplesmente seguir as
[instruções da documentação do CKAN](https://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html)
e usar as opções padrão de configuração onde for possível.

## Preparação e dependências

Primeiro, assegure-se de ter bastante espaço livre em disco, já que essas
imagens comem um bocado de espaço. Como são baseadas no Ubuntu 16.04, que já
é bem velho agora, é mais provável que você esteja usando um sistema operacional
mais recente que isso. Por isso o Docker terá que baixar muita coisa para
compensar pela diferença. No meu caso, estou usando o Ubuntu 18.04, então a
instalação completa gastou mais ou menos 5 GB de espaço.

Os volumes Docker, por padrão, são armazenados em `/var/lib/docker`. A qualquer
momento depois da instalação, você pode verificar quais volumes Docker você
tem com o comando

```bash
$ docker volume ls
```

Você também pode usar

```bash
$ docker volume inspect [volume]
```

para ver onde os arquivos que estão dentro de `[volume]` estão de fato
armazenados (sob a variável `Mountpoint`). Para mais informações, veja a
[documentação do Docker sobre volumes](https://docs.docker.com/engine/tutorials/dockervolumes/).

Você também precisa instalar o Docker e o Docker Compose, caso não já o tenha
feito. Estou tomando como base o Ubuntu 18.04, mas deve ser semelhante em
outros sistemas Ubuntu baseados em sistemas GNU/Linux. Simplesmente faça

```bash
$ sudo apt install docker.io docker-compose
```

ou siga as instruções na documentação do
[Docker](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/)
e do
[Docker Compose](https://docs.docker.com/compose/install/).

## Construindo as imagens de Docker

Primeiro precisamos fazer o download do repositório CKAN a partir do Github.
Vá para um diretório de sua escolha e faça o clone do repositório. A depender
da sua velocidade de download, isso pode demorar um pouco.

```bash
$ cd /path/to/my/projects
$ git clone https://github.com/ckan/ckan.git
```

O repositório tem todas as versões atuais e passados sob controle de versões,
por isso escolhemos a versão (supostamente) estável 2.9.0, fazendo o
*checkout* da sua *tag* correspondente:

```bash
$ cd ckan
ckan$ git checkout tags/ckan-2.9.0
```

Em seguida, copie `contrib/docker/.env.template` para `contrib/docker/.env`.
Ele contém algumas variáveis de ambiente que você pode querer mudar, como a
URL do site, porta e senhas. Se você está só vendo como o CKAN funciona, i.e.,
em um ambiente que não é de produção, está tudo bem deixá-lo como está (com as
configurações padrão).

Agora construiremos as imagens de Docker. Este passo demora um bocado de
tempo, consome bastante espaço em disco e faz o download de muitas imagens
e pacotes. Por isso, você pode querer ir fazer outra coisa enquanto ele
roda.

**Spoiler:** vamos encontrar um problema no próximo passo, depois de
construir a imagem. Para economizar um tempo, você pode não querer executar
o próximo passo e ir diretamente para [o conserto](#a-correcao).

```bash
ckan$ cd contrib/docker
ckan/contrib/docker$ docker-compose up -d --build
```

Em seguida, vamos reiniciar o *cluster* de containers com:

```bash
ckan/contrib/docker$ docker-compose restart ckan
WARNING: The CKAN_MAX_UPLOAD_SIZE_MB variable is not set. Defaulting to a blank string.
Restarting ckan ... done
```

Verifique se o container está rodando:

```bash
ckan/contrib/docker$ docker ps | grep ckan
67693ebf5e92        docker_ckan                 "/ckan-entrypoint.sh…"   49 seconds ago       Up 6 seconds              0.0.0.0:5000->5000/tcp   ckan
```

E os logs de sistema

```bash
ckan/contrib/docker$ docker-compose logs -f ckan
WARNING: The CKAN_MAX_UPLOAD_SIZE_MB variable is not set. Defaulting to a blank string.
Attaching to ckan
ckan          | db:5432 - accepting connections
ckan          | Command 'db' not known (you may need to run setup.py egg_info)
ckan          | Known commands:
ckan          |   create       Create the file layout for a Python distribution
ckan          |   exe          Run #! executable files
ckan          |   help         Display help
ckan          |   make-config  Install a package and create a fresh config file/directory
ckan          |   points       Show information about entry points
ckan          |   post         Run a request for the described application
ckan          |   request      Run a request for the described application
ckan          |   serve        Serve the described application
ckan          |   setup-app    Setup an application, given a config file
ckan          | db:5432 - accepting connections
ckan          | Command 'db' not known (you may need to run setup.py egg_info)
ckan          | Known commands:
ckan          |   create       Create the file layout for a Python distribution
ckan          |   exe          Run #! executable files
ckan          |   help         Display help
ckan          |   make-config  Install a package and create a fresh config file/directory
ckan          |   points       Show information about entry points
ckan          |   post         Run a request for the described application
ckan          |   request      Run a request for the described application
ckan          |   serve        Serve the described application
ckan          |   setup-app    Setup an application, given a config file
ckan exited with code 2
```

Ops. Temos um problema. Aparentemente, o comando `db` não está sendo
encontrado em algum lugar.

<figure markdown="1">
![Slide da apresentação do CKAN, mostrando uma foto feita por Petras Gagilas de um bebê demonstrando frustração]({{ 'assets/images/2020/09/frustration-slide.jpg' | relative_url }})
<figcaption>Oh, não! O que vamos fazer?</figcaption>
</figure>

### A correção

Procurando por aí, encontrei no *issue tracker* do CKAN no Github que esse
erro acontece devido a [um bug](https://github.com/ckan/ckan/issues/5572) nesta
versão do CKAN. Aparentemente, ele já foi corrigido por [esse *pull
request*](https://github.com/ckan/ckan/pull/5381) do Mark Stuart que já foi
aceito e mesclado com a *master branch* (que logo será [renomeada para
*main*](https://github.com/github/renaming), como tudo no Github).
Entretanto, essa correção ainda não foi incorporada em um *release* estável.

Então ficamos com algumas alternativas para prosseguir:

1. Usar uma versão mais antiga do CKAN, como a 2.8.5, e torcer para que ela
   não tenha o bug;
2. usar outro método de instalação que não seja com Docker;
3. usar a *master branch*, que pode conter funcionalidades experimentais e
   ainda não é código estável; ou
4. usar a versão 2.9.0, mas aplicar um *patch* só para essa correção.

Decidimos por usar esta última,
[como sugerido por mabah-mst naquela *issue*](https://github.com/ckan/ckan/issues/5572#issuecomment-693263908),
executando os seguintes comandos:

```bash
ckan/contrib/docker$ cd ../..
ckan$ git checkout tags/ckan-2.9.0
#Aplicar correção para que o CKAN passe a iniciar no docker-compose: https://github.com/ckan/ckan/pull/5381
ckan$ git diff 9abeaa1b7d2f6539ade946cc3f407878f49950eb^ 9abeaa1b7d2f6539ade946cc3f407878f49950eb | git apply
```

Dessa forma, obtemos o *release* estável 2.9.0 e *somente* esta correção, e
não quaisquer outras funcionalidade experimentais que possivelmente podem
ter sido incorporadas na *master branch*.

Agora, vamos dar o *build* nisso novamente. E esperar de novo...

```bash
ckan$ cd contrib/docker
ckan/contrib/docker$ docker-compose up -d --build
```

Agora verifique para ver se o container está mesmo rodando:

```bash
ckan/contrib/docker$ docker ps | grep ckan
582466833e55        docker_ckan                 "/ckan-entrypoint.sh…"   4 hours ago         Up 4 hours             0.0.0.0:5000->5000/tcp   ckan
```

e abra um navegador na porta padrão, que é 5000 (`localhost:5000`), para dar
uma olhada.

E *Voilà*! O CKAN está rodando!

<figure markdown="1">
![ckan Datasets Organizations Groups About search box Welcome to CKAN]({{ 'assets/images/2020/09/default-ckan.gif' | relative_url }})
<figcaption>A tela inicial de uma instalação padrão do CKAN.</figcaption>
</figure>

## Configuração básica

Se o idioma que você vai usar no site não for o inglês, agora é uma boa hora
para mudar a língua padrão. Para isso, você precisa encontrar e editar o
arquivo `production.ini`. Para descobrir onde ele está, digite

```bash
ckan/contrib/docker$ docker volume inspect docker_ckan_config 
[
    {
        "CreatedAt": "2020-09-29T10:16:51-03:00",
        "Driver": "local",
        "Labels": {
            "com.docker.compose.project": "docker",
            "com.docker.compose.volume": "ckan_config"
        },
        "Mountpoint": "/var/lib/docker/volumes/docker_ckan_config/_data",
        "Name": "docker_ckan_config",
        "Options": null,
        "Scope": "local"
    }
]
```
e você poderá ver que está sob `Mountpoint`, em
`/var/lib/docker/volumes/docker_ckan_config/_data`. As permissões do diretório
pertencem ao usuário *root*, então você precisará editá-lo usando `sudo` (ex.:
`sudo vim /var/lib/docker/volumes/docker_ckan_config/_data/production.ini`
ou
`sudo gedit /var/lib/docker/volumes/docker_ckan_config/_data/production.ini`).

Procure pela seção com o nome *"Internationalisation Settings"*. Mude as
variáveis `ckan.locale_default` e `ckan.locale_order` dessa maneira.

```ini
## Internationalisation Settings
ckan.locale_default = pt_BR
ckan.locale_order = en pt_BR ja it cs_CZ ca es fr el sv sr sr@latin no sk fi ru de pl nl bg ko_KR hu sa sl lv
ckan.locales_offered =
ckan.locales_filtered_out = en_GB
```

**Curiosidade:** a primeira tradução que foi feita do CKAN para o português
brasileiro foi em 2009, feita por este que vos escreve. Eu também mantive
a tradução atualizada, por mais alguns anos, à medida em que novas versões
do CKAN foram sendo lançadas.

Reinicie o CKAN e você deve ser capaz de ver o novo idioma padrão em
funcionamento.

```bash
ckan/contrib/docker$ docker-compose restart ckan
```

### Habilitando o primeiro usuário

Agora precisamos criar o usuário administrador para começar a trabalhar com
o CKAN.

Damos uma olhada na
[documentação](https://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html#create-ckan-admin-user)
para descobrir o comando para criar um administrador, por exemplo, com o
usuário zedasilva.

```bash
ckan/contrib/docker$ docker exec -it ckan /usr/local/bin/ckan-paster --plugin=ckan sysadmin -c /etc/ckan/production.ini add zedasilva
Command 'sysadmin' not known (you may need to run setup.py egg_info)
Known commands:
  create       Create the file layout for a Python distribution
  exe          Run #! executable files
  help         Display help
  make-config  Install a package and create a fresh config file/directory
  points       Show information about entry points
  post         Run a request for the described application
  request      Run a request for the described application
  serve        Serve the described application
  setup-app    Setup an application, given a config file
```

Mas, que coisa, isso não funciona! O comando `sysadmin` não é reconhecido.
Pudemos constatar que é
[um outro bug](https://github.com/ckan/ckan/issues/5621). Desta vez, eu tive
que abrir por mim mesmo uma nova *issue*. Dois dias depois, o
[Konstantin Sivakov](https://github.com/ckan/ckan/issues/5621#issuecomment-699672432)
chamou atenção para o fato que esse comando em particular
[foi alterado no CKAN 2.9](https://docs.ckan.org/en/2.9/changelog.html#migration-notes):

> A velha interface de comando do paster foi removida em substituição ao novo
> comando ckan. Na maioria dos casos, a sintaxe dos comandos e dos subcomandos
> é a mesma, mas o parâmetro `-c` ou `--config` para apontar para o arquivo
> ini precisa ser fornecido imediatamente após o comando ckan, ex.:
> 
> `ckan -c /etc/ckan/default/ckan.ini sysadmin`
> 

Um sinal de uma comunidade saudável de software livre e de código aberto é se
e em quanto tempo se obtém uma resposta, quando se encontra um problema como
esse. No nosso caso, levou apenas dois dias, o que significa que a comunidade
CKAN está bem ativa e solícita. Graças ao
[Brett](https://github.com/ckan/ckan/issues/5621#issuecomment-699862976), aqui
está a solução:

```bash
ckan/contrib/docker$ docker exec -it ckan
$ source /usr/lib/ckan/venv/bin/activate
(venv) $ ckan -c /etc/ckan/production.ini sysadmin add administrador email=administrador@localhost name=administrador
```

É claro que você pode (e deve) mudar o nome de usuário e o e-mail aqui. O
endereço de e-mail pode ser usado mais tarde, por exemplo, caso você esqueça
a sua senha e precise recuperá-la, sem ter que acessar a linha de comando no
servidor novamente. Se tudo correr bem, o sistema deve pedir que você insira
uma senha e a confirme, digitando-a mais uma vez.

### Configuração do administrador do site pela web

Agora podemos fazer o login no CKAN e começar a ajustar as configurações que
podem ser definidas pela interface web. Abra `localhost:5000` em um navegador.

<figure markdown="1">
![ckan Acessar, Nome de usuário, Senha, Lembre me]({{ 'assets/images/2020/09/ckan-login-pt.gif' | relative_url }})
<figcaption>A tela de login do CKAN.</figcaption>
</figure>

Depois de fazer o login, você deve ver uma nova barra no topo com o seu nome
de usuário e alguns elementos de interface nos quais você pode clicar.

<figure markdown="1">
![ckan: Conjuntos de dados, Organizações, Grupos, Sobre]({{ 'assets/images/2020/09/ckan-top-bar-pt.png' | relative_url }})
<figcaption>A barra de topo do usuário logado.</figcaption>
</figure>

Clique o ícone do martelo 🔨 ali e na aba "configuração" você poderá ajustar
mais configurações, tais como o nome do site, a logo, descrição e cores.
Escolha um layout para a página inicial. Você pode também especificar um CSS
customizado para personalizar ainda mais a aparência e a sensação do seu
catálogo de dados.

<figure markdown="1">
![ckan: Configuração, Título do Site, Estilo, Lema do site, Logo do site, Sobre, Texto introdutório, CSS customizado, Homepage]({{ 'assets/images/2020/09/ckan-site-config-pt.gif' | relative_url }})
<figcaption>A tela de configuração do CKAN.</figcaption>
</figure>

### Configurando organizações e grupos

Como um administrador do site, você também é capaz de inserir novos conjuntos
de dados no seu catálogo. Mas, normalmente, você iria querer distribuir essa
carga de trabalho para outras pessoas, com um papel mais focado. Há muitas
maneiras diferentes de se organizar isso. Se você tem uma instituição de média
a grande, você pode querer criar "organizações" para cada um dos dos seus
departamentos, de maneira que cada uma gerencie os seus próprios conjuntos de
dados. As organizações no CKAN são apenas uma maneira de se gerenciar uma
grande quantidade de conjuntos de dados, delegando responsabilidades a cada
departamento sobre os seus respectivos conjuntos de dados.

Este pode ser um bom momento para se configurar o serviço de envio de e-mails,
para que o CKAN seja capaz de enviar e-mails para as pessoas, quando você
criar usuários e também para que o sistema de recuperação de senhas funcione
adequadamente. Para isso, você precisa editar o arquivo `.env` na seguinte
seção:

```ini
# Email settings
CKAN_SMTP_SERVER=smtp.corporateict.domain:25
CKAN_SMTP_STARTTLS=True
CKAN_SMTP_USER=user
CKAN_SMTP_PASSWORD=pass
CKAN_SMTP_MAIL_FROM=ckan@localhost
```

Use o endereço e as credenciais do seu próprio servidor de SMTP aqui. Em
seguida, reinicie o CKAN com

```bash
ckan/contrib/docker$ docker-compose restart ckan
```

para que as mudanças façam efeito. Agora podemos acrescentar a primeira
organização:

<figure markdown="1">
![Organizações: Adicionar uma Organização, pesquisar organizações, Não foram encontradas organizações]({{ 'assets/images/2020/09/ckan-organizations-pt.png' | relative_url }})
<figcaption>A tela de organizações.</figcaption>
</figure>

Clique em "Organizações", e em seguida no botão "Adicionar uma Organização".

<figure markdown="1">
![Criar uma Organização: Nome, Descrição, Imagem]({{ 'assets/images/2020/09/ckan-new-organization-pt.png' | relative_url }})
<figcaption>Adicionando uma nova organização.</figcaption>
</figure>

Isso é bastante simples. Adicione um nome, uma descrição e opcionalmente uma
imagem para representá-la. Clique "Criar Organização". Então, clique
imediatamente em "🔧 Gerenciar", então na aba "👥 Membros", em seguida em
"Adicionar Membro". Escolha o papel "Administrador", já que este será o
administrador desta organização. Sob "novo usuário", preencha o endereço de
e-mail da pessoa. Ela deve receber uma mensagem com o link para criar o seu
novo usuário, que receberá automaticamente as permissões que você definir aqui
(neste caso, o pepel de administrador desta organização, que é diferente do
administrador do site em geral que estamos usando agora).

<figure markdown="1">
![Adicionar membro: Usuário Existente: Se você quer adicionar um usuário existente, busque pelo nome dele abaixo; nome de usuário. Ou. Novo Usuário: Se você quer convidar um novo usuário, inclua o endereço de email dele; endereço de e-mail. Papel: membro.]({{ 'assets/images/2020/09/ckan-add-member-pt.gif' | relative_url }})
<figcaption>Adicionando um novo usuário.</figcaption>
</figure>

O(a) administrador(a) da organização terá então que seguir o link em seu e-mail,
ativar a sua conta e fazer login. Depois disso, ele(a) terá que seguir o mesmo
procedimento acima para adicionar outros usuários com o papel de "Editor".
Após ativar suas próprias contas, os editores poderão criar e editar conjuntos
de dados no CKAN dentro de suas respectivas organizações.

Outra maneira de organizar os conjuntos de dados no catálogo de dados é criar
grupos temáticos (ex.: saúde, educação, transporte, etc.). Isso é totalmente
opcional, mas se você quiser usá-los pode ir a qualquer momento em "Grupos" no
menu do topo, clicar em "Adicionar grupo" e preencher as informações do grupo:
nome, descrição e uma imagem.

<figure markdown="1">
![Criar um grupo: Nome, Descrição, Imagem]({{ 'assets/images/2020/09/ckan-create-group-pt.png' | relative_url }})
<figcaption>Adicionando um novo grupo.</figcaption>
</figure>

Depois disso, o grupo deve estar disponível para a escolha dos editores,
quando forem criar ou editar conjuntos de dados.

Para mais informações sobre como gerenciar organizações e conjuntos de dados,
veja
[a seção correspondente do Guia do Administrador de Sistema do CKAN](https://docs.ckan.org/en/2.9/sysadmin-guide.html#managing-organizations-and-datasets).

Você também deve capacitar os editores sobre como criar um conjunto de dados
e operar o CKAN. Pessoas com o papel de editor devem ser alguém que entenda
bem sobre os dados que estão adicionando, pois eles precisarão descrevê-los
adequadamente e em linguagem clara para os utilizadores finais do portal de
dados, de uma maneira que seja fácil de entender.
Para instruções sobre como criar e editar conjuntos de dados, a documentação
do CKAN tem um
[Guia do Utilizador](https://docs.ckan.org/en/2.9/user-guide.html).

## Colocando em ambiente de produção

Isso cobre as configurações básicas. Antes de colocar em ambiente de produção,
é especialmente importante que você edite e revise todas as configurações em
ambos os arquivos `.env` e `production.ini`. Por favor leia a seção
"[passos para a produção](https://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html#steps-towards-production)"
do Guia de Manutenção na documentação do CKAN para mais informações.

## Considerações finais

Em geral, tivemos alguns problemas com a versão 2.9.0, já que as instruções
da documentação não funcionaram de imediato. Entretanto, com a ajuda da
comunidade do CKAN, fomos capazes de superar esses obstáculos e terminar com
uma instalação da última versão do CKAN, em pleno funcionamento em um ambiente
Docker.

**Editado:** para uma outra maneira possível de se instalar o CKAN 2.9.0 com
Docker, por favor leia esta
[postagem de blog](https://blog.thenets.org/install-ckan-using-docker/) (em
inglês) do Luiz Felipe Costa. O Luiz desenvolveu a personalização do CKAN para
o portal [dados.gov.br](https://dados.gov.br) na
[revisão de 2017](https://wiki.dados.gov.br/ProdutoGT3_Portal%20de%20Dados%20Abertos.ashx#%E2%9E%83_E%C2%BA_Ciclo_CABH_15),
da qual eu fui *product owner*, e eu recomendo os seus serviços.
