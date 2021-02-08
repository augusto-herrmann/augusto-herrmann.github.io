---
layout: post
title: "Como construir um ambiente personalizado para o Jupyter no Docker"
author: "Augusto Herrmann"
lang: pt
ref: 2021-02-08-how-to-build-custom-environment-for-jupyter-in-docker
category: [pt, blog]
tags: [
  jupyter,python,docker,containers,jupyter lab,jupyter notebook,
  requirements,pacotes
]
cover: /assets/images/2021/02/jovian-cloudscape-juno-2018.jpeg
snippet-image: /assets/images/2021/02/jovian-cloudscape-juno-2018.jpeg
desc: >-
  Rodar o Jupyter Lab e o Jupyter Notebook dentro de um container Docker
  é uma boa maneira de manter os seus ambientes isolados do seu sistema.
  Embora existam imagens Docker prontas para fazer isso, infelizmente
  não é tão óbvio como configurá-las e preparar um ambiente personalizado
  com os pacotes Python de sua preferência. Veja aqui como você pode
  construir um ambiente flexível e customizado para os seus próprios
  cadernos.
image-credits: "Juno probe / NASA"
---

Se você tem desenvolvido software nos últimos anos, você provavelmente
teve algum contato com o uso de containers não apenas para fazer o
*deploy*, mas também durante o desenvolvimento para ter certeza de que
o seu ambiente é totalmente reproduzível em sistemas diferentes.

Também é muito popular nos meios de ciência de dados, visualização de
dados e outros relacionados usar Python e
[Jupyter](https://jupyter.org/) Notebooks e Jupyter Lab para explorar e
experimentar com os dados. Algumas pessoas
[criticam o Jupyter por frequentemente resultar em trabalhos não reproduzíveis](https://adamrule.com/files/papers/chi_2018.pdf),
algo muito importante para o método científico, pois o ambiente de
desenvolvimento pode ser diferente daquele que o vai reproduzir e as
células podem ser executadas fora de ordem. Por exemplo, em
[um experimento](https://blog.jetbrains.com/datalore/2020/12/17/we-downloaded-10-000-000-jupyter-notebooks-from-github-this-is-what-we-learned/)
feito pela equipe Datalore do Jetbrains Datalore no ano passado que
baixou quase 10 milhões de cadernos do Github, eles descobriram que 36%
desses cadernos eram inconsistentes, isto é, eram executados em uma
ordem não linear.

Por outro lado, se o seu ambiente estiver definido em um container
[Docker](https://en.wikipedia.org/wiki/Docker_(software)) e você tomar
o cuidado de fazer a boa prática de executar as células na ordem
apropriada, os cadernos podem ser completamente reproduzíveis.

Pode não ser tão óbvio como fazê-lo, todavia. Por isso, aqui está um
guia passo a passo de como usar o Jupyter Lab e o Jupyter Notebook
dentro do Docker com os pacotes Python de sua escolha.

Este guia foi escrito pensando em um sistema baseado em GNU-Linux e foi
testado no Ubuntu 18.04 e 20.04. Ele deve funcionar em outros sistemas
baseados em GNU-Linux. Todavia, se você estiver usando Windows ou MacOS,
você terá que fazer algumas adaptações para funcionar, principalmente em
relação às operações de linha de comando e variáveis de ambiente, mas
isso não é abordado neste guia.

## Preparações

Antes de começar, certifique-se de que o
[Docker](https://docs.docker.com/engine/install/) e o
[Docker Compose](https://docs.docker.com/compose/install/) estão
instalados.

## Escolhendo uma imagem base

O
*[Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)*
fornece algumas imagens prontas para rodar e algumas
[receitas](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/recipes.html#using-pip-install-or-conda-install-in-a-child-docker-image)
para criar a sua própria imagem de Docker herdando a partir destas (o
que eles chamam de imagem Docker filha).

Para isso, precisamos primeiro escolher uma imagem base da qual herdar.
Para este exercício vamos usar a `jupyter/scipy-notebook`, que inclui
o [Pandas](https://pandas.pydata.org/), o [NumPy](https://numpy.org/)
e mais algumas coisas. Entretanto, dê uma olhada na seção de
[seleção de imagem](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html)
na documentação do *Jupyter Docker Stacks* para ver outras opções.

Então vamos criar um `Dockerfile` para construir a imagem Docker
personalizada e a seguinte linha para definir a imagem base:

```dockerfile
FROM jupyter/scipy-notebook
```

Se você não quiser criar um novo `Dockerfile` do zero, você também pode
clonar
[este repositório de exemplo](https://github.com/augusto-herrmann/docker-jupyter-extensible)
a partir do Github, que tem um `Dockerfile` pronto para uso.

## Configurando os *locales*

{% assign linked_post=site.posts | where:"ref", "2021-02-05-how-to-deal-with-international-data-formats-in-python" | where:"lang", page.lang %}
Se você algum dia for trabalhar com dados de outros *locales* que não
sejam os EUA,
[você provavelmente deveria configurar um ou mais outros *locales*]({{linked_post.first.url}}).
Por exemplo, isso vai tornar mais fácil trabalhar com separadores de
casas decimais diferentes ou com os nomes dos dias da semana e dos meses
do ano em diferentes idiomas.

Para este exercício, vamos configurar os *locales* do sistema para usar
ambos os *locales* en_US.UTF-8 (inglês, EUA) e pt_BR.UTF-8 (português
brasileiro). A seguinte seção do `Dockerfile` faz exatamente isso.

```dockerfile
# instala os locales que você quiser usar
RUN set -ex \
   && sed -i 's/^# en_US.UTF-8 UTF-8$/en_US.UTF-8 UTF-8/g' /etc/locale.gen \
   && sed -i 's/^# pt_BR.UTF-8 UTF-8$/pt_BR.UTF-8 UTF-8/g' /etc/locale.gen \
   && locale-gen en_US.UTF-8 pt_BR.UTF-8 \
   && update-locale LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 \
```

## Escolhendo os seus pacotes Python

Em seguida, nós vamos escolher os pacotes Python que estarão disponíveis
para o Jupyter dentro do ambiente. Neste exemplo, escolhemos a ferramenta
de visualização de dados chamada [Plotly](https://plotly.com/python/) e
o pacote de traçar mapas chamado
[Folium](https://python-visualization.github.io/folium/). Esta é a
seção do `Dockerfile` onde definimos isso.

```dockerfile
# instala os pacotes Python que você usa frequentemente
RUN set -ex \
   && conda install --quiet --yes \
   # escolhe os pacotes Python que você precisa
   'plotly==4.9.0' \
   'folium==0.11.0' \
   && conda clean --all -f -y \
   # instala as extensões do Jupyter Lab que você precisa
   && jupyter labextension install jupyterlab-plotly@4.9.0 --no-build \
   && jupyter lab build -y \
   && jupyter lab clean -y \
   && rm -rf "/home/${NB_USER}/.cache/yarn" \
   && rm -rf "/home/${NB_USER}/.node-gyp" \
   && fix-permissions "${CONDA_DIR}" \
   && fix-permissions "/home/${NB_USER}"
```

Substitua-os ou adicione os pacotes Python e extensões do Jupyter Lab
que você quiser.

## Construindo o container

Este passo é muito fácil de se fazer, mas pode demorar bastante para
terminar. Simplesmente execute o seguinte comando:

```sh
$ docker build --rm -t docker-jupyter-extensible .
```

e vá fazer um lanche ou fazer alguma outra coisa e volte depois de um
tempo.

## Corrigindo as permissões

Um problema comum ao montar uma pasta do *host* dentro do container é
que os donos dos arquivos frequentemente não se correspondem. Então
você fica ou sem acesso à pasta ou com somente leitura. Para corrigir
isso, precisamos configurar o usuário e o grupo usados dentro do
container para ter os mesmos números de id que o usuário e grupo que
você estiver usando no *host*. Pode parecer complicado, mas com essas
imagens é algo muito fácil de se fazer.

Apenas crie um arquivo chamado `.env`, rodando o seguinte comando:

```sh
$ printf "UID=$(id -u)\nGID=$(id -g)\n" > .env
```

Isso vai permitir que você use a pasta `notebooks` tanto dentro como
fora do container.

## Executando o container

Está pronto! A cada vez que você quiser iniciar o Jupyter, apenas rode o
container com o comando:

```sh
$ docker-compose up
```

Você deve ver as mensagens do container no terminal. Se tudo correr bem,
você deve ver um link começando com `http://127.0.0.1:8888` que também
contém um *token* de acesso. Abra esse link em um navegador para usar o
Jupyter Notebook. Se, em vez disso, você quiser usar o Jupyter Lab, é
só trocar o início da URL para
`http://127.0.0.1:8888/lab`, mas mantenha tudo depois disso, incluindo
o *token* de acesso.

<figure markdown="1">
![Tela do terminal mostrando a saída do container Jupyter se iniciando.]({{ 'assets/images/2021/02/docker-jupyter-in-terminal.gif' | relative_url }})
<figcaption>A saída do terminal ao iniciar o container mostra a URL e o
token para abrir no navegador o Jupyter Lab e o Jupyter Notebook.</figcaption>
</figure>

Para verificar que os pacotes foram corretamente instalados e
configurados, apenas abra um novo caderno e os importe. Veja, por
exemplo, o
[Plotly Express](https://plotly.com/python/plotly-express/):

<figure markdown="1">
![Uma janela do navegador com o Jupyter Lab rodando o Plotly Express.]({{ 'assets/images/2021/02/jupyter-lab-with-plotly-express.gif' | relative_url }})
<figcaption>Um exemplo de gráfico do Plotly Express rodando dentro do
nosso novo container Docker.</figcaption>
</figure>

Agora divirta-se com o seu novo Jupyter Lab ou Jupyter Notebook!

Se, mais tarde, você quiser acrescentar quaisquer novos pacotes, só vá
para
[o passo “escolhendo os seus pacotes”](#escolhendo-os-seus-pacotes-python),
faça as alterações que deseja e siga a partir dali, construindo o
container novamente.
