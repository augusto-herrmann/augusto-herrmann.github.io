---
layout: post
title: >-
  Cadastro (Im)positivo: Saiba quais dos seus dados o Banco Central está
  compartilhando
author: Augusto Herrmann
lang: pt
ref: 2023-09-22-impositive-registry-know-which-data-of-yours-the-central-bank-is-sharing
category: [pt, blog]
tags: [brasil, privacidade, dados pessoais, banco central, birôs de crédito, cadastro positivo]
cover: /assets/images/2023/09/mufid-majnun-LVcjYwuHQlg-unsplash.jpg
snippet-image: /assets/images/2023/09/mufid-majnun-LVcjYwuHQlg-unsplash.jpg
desc: >-
  Se você é cliente bancário no Brasil, o Banco Central está compartilhando
  com os birôs de crédito dados sobre o seu relacionamento com o seu banco,
  bem como detalhes de quaisquer operações de crédito. E mesmo que você não
  seja um cliente bancário, ele recebe de volta informações sobre os seus
  pagamentos a concessionárias como os de contas de água e energia.
image-credits: Mufid Majnun / Unsplash
---


{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2023-09-08-impositive-registry-brazils-central-bank-will-share-your-data-with-credit-reporting-agencies" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

Em sequência ao [artigo anterior]({{ reference_post.url | relative_url }}),
descobrimos com ajuda do Bruno Morassutti da
[Fiquem Sabendo](https://fiquemsabendo.com.br/) que o inteiro teor dos
acordos entre o Banco Central do Brasil (BCB) e os birôs de crédito está
disponível na seção de transparência do site da instituição. Todos eles
têm o mesmo conteúdo, exceto pela identificação do birô de crédito, os
respectivos departamentos internos responsáveis e signatários. Todos os
cinco também compartilham o mesmo dia de assinatura: 4 de setembro
de 2023. Eis os links para cada um deles:

* [Acordo com Boa Vista Serviços S.A.](https://www.bcb.gov.br/content/acessoinformacao/acordos_docs/ACORDO_64_2023-BCB_DESIG_ACT_BVS.pdf)
* [Acordo com QUOD Gestora de Inteligência de Crédito S.A.](https://www.bcb.gov.br/content/acessoinformacao/acordos_docs/ACORDO_61_2023-BCB_DESIG_ACT_QUOD.pdf)
* [Acordo com Serasa S.A.](https://www.bcb.gov.br/content/acessoinformacao/acordos_docs/ACORDO_71_2023-BCB_DESIG_ACT_Serasa.pdf)
* [Acordo com SPC Brasil](https://www.bcb.gov.br/content/acessoinformacao/acordos_docs/ACORDO_69_2023-BCB_DESIG_ACT_SPC.pdf)
* [Acordo com TransUnion Brasil Sistemas em Informática Ltda](https://www.bcb.gov.br/content/acessoinformacao/acordos_docs/ACORDO_10_2023-BCB_DESIG_ACT_TU.pdf)

## Dados que os birôs de crédito enviam ao BCB

Os birôs de crédito enviam os seguintes dados ao BCB, conforme descrito
na cláusula segunda do acordo. A primeira troca de dados fornecerá dados
relativos aos **12 meses** anteriores.

### Mensalmente

* informações sobre todos os seus pagamentos de contas de concessionárias
  * água e esgoto
  * eletricidade
  * gás
  * telecomunicações

### Trimestralmente

* seu *score* de crédito

## Dados que o BCB envia aos birôs de crédito

O BCB enviará **mensalmente** os seguintes dados aos birôs de crédito,
como estabelecido na cláusula terceira do acordo. A primeira troca de
dados fornecerá dados relativos aos **24 meses** anteriores.

* identificação do cliente, tipo de cliente e data de início de
  relacionamento com a instituição financeira
* qualquer crédito contratado, incluindo a identificação da instituição
  financeira, tipo de operação, número do contrato, valor, data de
  contratação e de vencimento e número de prestações
* quaisquer garantias oferecidas, incluindo o tipo e quantidade
* dados contábeis da operação de crédito, incluindo saldo devedor, valor
  e data de vencimento da próxima prestação

## Como se opor à transferência de dados

Se você quiser recusar a transferências dos seus dados, seu único recurso
é manifestar formalmente a sua oposição diretamente a qualquer dos
próprios birôs de crédito.

Você pode fazer isso online, por telefone, por carta ou até pessoalmente.
Mas todos eles exigem que você forneça muitas informações pessoais e
documentos, supostamente para que possam identificar você – apesar de
exigirem muito mais documentos e informações do que seria suficiente
para identificar alguém. Simplesmente apresentar um documento oficial
contendo o CPF deveria ser suficiente para isso. Todavia, há
[casos documentados](https://tecnoblog.net/responde/como-sair-do-cadastro-positivo-cancelar-entrada/)
em que eles também exigem um número de telefone, e-mail, endereço
residencial, data e local de nascimento, nomes dos pais, uma selfie e
outros.
