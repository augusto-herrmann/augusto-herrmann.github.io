---
layout: post
title: >-
  Como rodar o programa da declaração de imposto de renda 2024 no Ubuntu 20.04
author: Augusto Herrmann
lang: pt
ref: 2024-05-16-como-rodar-programa-declaracao-imposto-renda-2024-ubuntu-20-04
category: [pt, blog]
tags: [imposto, rfb, java, ubuntu, linux]
cover: /assets/images/2024/05/lion-ingo-stiller-3tkxfe2GocY-unsplash.jpg
snippet-image: /assets/images/2024/05/lion-ingo-stiller-3tkxfe2GocY-unsplash.jpg
desc: >-
  Saiba como instalar no Ubuntu 20.04 o programa de Declaração de Imposto de
  Renda da Pessoa Física (IRPF) da RFB, versão 2024, afetando o mínimo o
  resto do seu sistema.
image-credits: Ingo Stiller / Unsplash
---
Uma boa prática para manter o sistema operacional funcionando bem é manter
todas as aplicações que você precisa executar em ambientes isolados. Isso
evita que as dependências de um atrapalhem o funcionamento de outro,
isolando os componentes.

Essa é a lógica por trás de soluções de conteinerização, como o Docker,
e de alguns gerenciadores de aplicativos, como o Snap, desenvolvido pela
Canonical, empresa que faz a distribuição de Linux Ubuntu. Quando se
instala uma aplicação pelo Snap, por exemplo, ela passa a ser executada
em um ambiente isolado do resto do sistema operacional e todas as
bibliotecas e componentes utilizados por ela ficam dentro deste ambiente
isolado. Assim, se você instalar outra aplicação que precisa de outra
versão dos mesmos componentes, um não afetará o outro.


## O programa de declaração do IRPF

As cidadãs e os cidadãos brasileiros são obrigados todos os anos a
apresentar a Declaração de Imposto de Renda da Pessoa Física (IRPF) por
meio eletrônico, a qual pode ser feita por meio de acesso ao sistema web
da Receita Federal do Brasil (RFB), mediante login na plataforma Gov.br.
Ou então, pelo meio tradicional, que é baixar e instalar uma aplicação
Java para preencher a declaração no próprio computador e enviá-la pela
internet.

Esta aplicação pode ser baixada
[diretamente do site da RFB](https://www.gov.br/receitafederal/pt-br/centrais-de-conteudo/download/pgd/dirpf),
onde está disponível em três versões: para Windows, Max, Linux, e "multi".

Infelizmente nenhuma delas utiliza sistemas que isolem a aplicação do
resto do sistema operacional, como Docker ou Snap. As três primeiras
instalam o seu próprio Java, mas há o risco de apresentar conflitos com
outra versão do Java que você já tenha instalado usar outros programas
ou desenvolver software, por exemplo.

Uma outra alternativa seria instalar uma dessas versões dentro de uma
máquina virtual, usando uma ferramenta de virtualização como o Virtual
Box. Porém, isso normalmente envolve também o trabalho de instalar e
configurar o sistema operacional dentro dessa VM. Esse tipo de solução
não será abordado neste artigo.

Dentre as quatro opções oferecidas, a solução que menos interfere no
funcionamento do sistema operacional é a opção "multi", já que ela não
altera o Java do seu sistema operacional. Nesse caso, você mesmo ficará
responsável por providenciar um ambiente Java compatível com o programa.
Esta versão é um arquivo zip que deve ser descompactado em uma pasta de
sua escolha. Dentro há um arquivo `irpf.jar`. Para executá-lo basta
digitar em um terminal `java -jar irpf.jar`, desde que o Java apropriado
esteja instalado.


## Qual Java instalar?

O programa da RFB recomenda usar a versão 11 do Java, que
[é de 2018](https://en.wikipedia.org/wiki/Java_version_history#Java_11).
Se você já tem um Java mais novo instalado, isso pode ser um problema.
Mais adiante mostrarei qual foi a solução que encontrei.

A primeira tentativa que fiz foi criar um arquivo `docker-compose.yml`,
usar a imagem `openjdk:11` disponível no Docker Hub, mapear os volumes
do programa e da pasta onde ele grava a declaração. O programa roda em
interface gráfica, então também é preciso mapear volume e variável de
ambiente para que ele tenha acesso à
[interface gráfica do X11](https://en.wikipedia.org/wiki/X_Window_System).
Todavia, mesmo assim ainda estava dando erro de permissão do AWT para
acessar o X11. Acabei desistindo desta forma de usar.

O gerenciador de pacotes `apt` disponibiliza diversas versões do OpenJDK
para se instalar. Se você, como eu, não precisa do Java e normalmente
não tem ele instalado, o curso de ação mais lógico parecia ser instalar
logo a versão 11 e rodar o programa:

```bash
sudo apt-get update
sudo apt install openjdk-11-jre
```

Atenção para não confundir com o pacote `openjdk-11-jre-headless`. Esse
"*headless*" significa que é uma versão sem interface gráfica.
Infelizmente, mesmo instalando o pacote `openjdk-11-jre` com o comando
acima, ainda assim dá um erro de acesso ao X11.


### Encontrando a versão certa do OpenJDK

Experimentei instalar diversas outras versões do OpenJDK: 8, 13, 16, 17
e 21. Somente com a versão 21 funcionou a interface gráfica. Assim,
caso você já tenha instalado uma outra versão do OpenJDK, remova-a com
o comando `sudo apt remove openjdk-[versão]`, usando o número de versão
apropriado. Então instale o OpenJDK versão 21:

```bash
sudo apt-get update
sudo apt install openjdk-21-jre
```

O programa do IRPF vai reclamar da versão do Java, dizer que a versão 11
é recomendada, mas é possível ignorar e seguir em frente assim mesmo.
Contudo, a funcionalidade da declaração pré-preenchida não estará
disponível e mostrará uma mensagem afirmando que só funciona com o Java
11.


### A solução que funciona: duas versões do Java ao mesmo tempo

A solução que realmente funciona é instalar ambas as versões do OpenJDK,
tanto a versão 11 quanto a 21:

```bash
sudo apt-get update
sudo apt install openjdk-11-jre openjdk-21-jre
```

Para executar o programa IRPF da RFB com o Java 11, será necessário
chamar explicitamente a versão 11:

```bash
/usr/lib/jvm/java-11-openjdk-amd64/bin/java -jar irpf.jar
```

Com isso o programa funcionará normalmente. Aparentemente ter o OpenJDK
versão 21 instalado simultaneamente faz com que alguma dependência ou
configuração esteja presente para que o OpenJDK versão 11 consiga,
também, acessar a interface gráfica do X11.


### Desinstalação e limpeza

Após fazer e entregar a declaração, lembre-se de salvar e guardar os
comprovantes. Para desinstalar, basta fazer

```bash
sudo apt remove openjdk-11-jre openjdk-21-jre
```

e apagar a pasta onde você havia descompactado a versão "multi".

Caso você tivesse um outro Java instalado antes, agora é hora de
reinstalá-lo novamente.


## Conclusão

O ideal seria que a RFB disponibilizasse uma imagem Docker ou pacote
Span para o programa de declaração anual de IRPF. Assim, o programa
ficaria completamente isolado do resto do sistema.

Com algum esforço, creio que seja possível configurar um `Dockerfile` e
`docker-compose.yaml` de código aberto para fazer funcionar de forma
isolada. É um exercício interessante para quem tiver tempo de fazê-lo.

Por ora, a maneira aqui apresentada atende à necessidade de executar o
programa da RFB interferindo o mínimo no sistema operacional.
