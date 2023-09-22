---
layout: post
title: >-
  (Im)positive Register: Brazil's Central Bank will share your data with
  credit reporting agencies
author: Augusto Herrmann
lang: en
ref: 2023-09-08-impositive-registry-brazils-central-bank-will-share-your-data-with-credit-reporting-agencies
category: [en, blog]
tags: [brazil, privacy, personal data, central bank, credit reporting agencies, cadastro positivo]
cover: /assets/images/2023/09/mufid-majnun-LVcjYwuHQlg-unsplash.jpg
snippet-image: /assets/images/2023/09/mufid-majnun-LVcjYwuHQlg-unsplash.jpg
desc: >-
  Brazil's Central Bank will share with credit reporting agencies data
  about bank clients' loans and other financial data.
image-credits: Mufid Majnun / Unsplash
---

Brazil's Central Bank (BCB) has published this Monday in the Official
Gazette extracts from agreements with five major consumer
[credit reporting agencies](https://en.wikipedia.org/wiki/Credit_bureau)
in Brazil to share data about Brazilian bank clients:

* [Quod](https://www.in.gov.br/en/web/dou/-/extrato-de-acordo-de-cooperacao-507618196)
* [TransUnion](https://www.in.gov.br/en/web/dou/-/extrato-de-acordo-de-cooperacao-507572817)
* [Boa Vista Serviços](https://www.in.gov.br/web/dou/-/extrato-de-acordo-de-cooperacao-507547320)
* [Serviço de Proteção ao Crédito (SPC)](https://www.in.gov.br/web/dou/-/extrato-de-acordo-de-cooperacao-507559126)
* [Serasa](https://www.in.gov.br/web/dou/-/extrato-de-acordo-de-cooperacao-507493813)

The terms of the agreements state that they are to come into effect
immediately after this publication (which is September 4th, 2023), and
also state that they are to remain in effect indefinitely.

The agreements had been
[announced in March by the BCB](https://www.bcb.gov.br/detalhenoticia/668/noticia)
in a note on its website, without much fanfare, and to no effective
repercussion at all, considering that I couldn't find a single news
article that mentioned them.

The existence of such agreements for sharing data with credit reporting
agencies had been provided in a bylaw from 2022,
[Resolução CMN no. 5,037](https://www.bcb.gov.br/estabilidadefinanceira/exibenormativo?tipo=Resolu%C3%A7%C3%A3o%20CMN&numero=5037):

> Article 10.  The Central Bank of Brazil may make available to managers
> of databases registered under the terms of article 12 of Law No.
> 12,414, of June 9, 2011, the information of the SCR on credit
> operations in compliance or in progress of those registered in those
> databases, respecting the rules established in this Resolution and in
> complementary regulations issued by the Central Bank of Brazil.
> 
> (...)
> 
> § 3rd.  The availability of the information referred to in the caput is
> conditional on the establishment of an agreement between the database
> manager and the Central Bank of Brazil.
> 
> § 4th.  The agreement referred to in the 3rd. paragraph of this article
> shall establish the manner in which the exchange of information between
> the parties shall take place.

However, only someone who had been following very closely the Central
Bank's regulations on this sector is likely to have seen it coming. When
compared to the widespread, dragnet surveillance effect that these data
sharing agreements entail, which is bound affect most Brazilians, one
could very easily argue that the agreements will take many people by
surprise.


## What data will be shared?

The BCB will share with credit reporting agencies data contained in the
Credits Information System (SCR). The bylaw that regulates the system,
Resolução CMN no. 5,037, contains a non-exhaustive list of what it
considers to be credit operations, which are to be included in the
system. The list is long and hard to understand, let alone translate to
English, to anyone who isn't savvy in the financial sector jargon. But it
seems to include but not be limited to loans, mortgages, pawn and other
modes of financing.

According to BCB's
[description of the system](https://www.bcb.gov.br/estabilidadefinanceira/scr),
they receive this data monthly from financial institutions (public and
private banks) in order to monitor financial operations and prevent
crises. They also assert that it does not violate bank's secrecy and that
the client's privacy is preserved,

> as it requires that the financial institution obtains express
> authorization from the client in order to access information about
> him or her.

That may well apply to the case where someone is applying for a loan and
the bank offers to access SCR in order to ascertain risk, and for that it
obtains an express authorization directly from the client. However, that
does *not* seem to be the case with the data sharing with credit
reporting agencies enabled by those new agreements, as it does not seem
plausible that the agency would obtain express authorization from each
and every person in the registry before obtaining the data from SCR.

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2023-09-22-impositive-registry-know-which-data-of-yours-the-central-bank-is-sharing" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

**Update:** see [this later post]{{ reference_post.url | relative_url }}
for more accurate information on what
kind of data is being shared.

## With whom will the data be shared?

The credit reporting agencies are private data brokers that collect
personal and financial data about people and companies, maintaining large
databases of their financial information, and calculates credit scores
based on that data. They then sell access to credit scores and payment
history to third parties interested in that data.

[Brazil's data protection law](https://www.lexml.gov.br/urn/urn:lex:br:federal:lei:2018-08-14;13709)
(LGPD) does not require that credit reporting agencies in Brazil are
obtain consent from people in order to use their data (Article 7, X).
That alone means that citizens get weaker protection from the use that
those data brokers make from personal data, as long as they claim that
using the data is required for credit protection.

Furthermore, in 2019
[Complementary Law no. 166](http://www.planalto.gov.br/ccivil_03/LEIS/LCP/Lcp166.htm)
provided for automatic inclusion of every Brazilian citizen in the
(Im)positive Registry (in Portuguese, *Cadastro Positivo*), under an
opt-out regime. It means that, unless someone explicitly notifies the
credit reporting agencies that they want to be excluded from the
registry, their data will be included in this private financial dragnet
surveillance network. In order to exercise your right to opt-out,
however, you often have to provide them with even more personal
information, such as the CPF (Brazilian's unique universal identification
number), full name, date of birth, home address, e-mail, phone number,
and sometimes even a selfie. At least the law states that once excluded
from the registry in any one of the credit reporting agencies, all others
are obliged to also follow through with the removal from their own
databases.

Information on the (Im)positive Registry includes all sorts of payments
and loans. Even public facility operators, such as electricity, water and
sanitation and gas companies are obliged to send personal and financial
data about their customers to the credit reporting agencies.


### The supposed benefits of the (Im)positive Registry

At the time that law was enacted, a few privacy experts and
[consumer protection activist organizations](https://idec.org.br/cadastro-positivo)
criticized the mandatory and automatic inclusion. Part
[of](https://www.pressreader.com/brazil/folha-de-s-paulo/20190511/281663961451508)
[the](https://www.estadao.com.br/economia/claudio-considera/cadastro-impositivo-comeca-a-valer/)
[press](https://www1.folha.uol.com.br/opiniao/2019/05/o-cadastro-positivo-vai-reduzir-o-custo-do-credito-nao.shtml)
also seemed skeptical to the claim that the measure would reduce the cost
of credit: just because financial institutions would be able to assess
risk more precisely does not automatically mean they would lower interest
raters.

On the other hand, another part of the press just repeated the same
arguments presented by these companies' lobbies: that having everyone
automatically included in the (Im)positive Registry would improve
everyone's credit score and lower the bank spread, which is the
difference between the base interest rates paid in government bonds and
the interest rates practiced by banks to their clients.

That argument for the law is based on several wrong assumptions: that
everyone is interested in trading off their privacy for credit
worthiness, valuing the latter much higher than the former. That everyone
is interested in taking credit all the time, rather than at very specific
points in their lifetime, such as when purchasing a home. Or even that
people nowadays share everything about themselves and their lives on
social networks anyway and are not interested in their own privacy.

Even if, for the sake of argument, we take their reasoning at face
value, a
[report issued by BCB itself in 2021](https://www.bcb.gov.br/content/publicacoes/Documents/outras_pub_alfa/analise_dos_efeitos_do_cadastro_positivo.pdf)
has determined that, as an effect of the automatic inclusion of everyone
in the (Im)positive Registry,

> about 41% of people have migrated to a lower risk of credit category
> as a result of inclusion in the (Im)positive Registry, 33% have
> remained in the same risk category, and 26% have migrated to a greater
> risk category.

While some people (41%) have had improvements on the credit assessment as
a result of using this data, a much higher proportion (59%) have either
remained the same or have had their creditworthiness reduced. This does
not seem like an advantageous tradeoff for most people, if it means that
they have to give up on the privacy of their personal and financial data.

As for the behavior of bank spreads,

> it found out that in comparison to the new borrowers who did not have
> scores based on the Positive Register, those who had them had an
> average reduction of 10.4% in the spreads of non-payroll personal loan
> operations. This decrease is equivalent to 31 p.p., when considering
> the average interest rate of 299% per year observed in this sample of
> operations.

Banks have been offering loans, according to this empirical study, during
that time period, with a "discount" of only 31 percent points out of the
exorbitant average interest rate of 299% a year. That seems way too
little, especially considering that the period measured had been very
atypical when considering interest rates in Brazil. In 2020 and 2021,
with a reasoning that they need to stimulate the economy during the
pandemic, the Monetary Policy Council had reduced the base interest rate
to
[a historic all-time low of less than 2% per year](https://www.bcb.gov.br/controleinflacao/historicotaxasjuros).
This is even lower than the inflation rate measured for the period,
counting as
[an effective negative rate](https://www.correiobraziliense.com.br/economia/2020/12/4897777-saiba-por-que-a-era-dos-juros-a-2--deve-acabar-em-2021.html)
for the first time in decades, if not ever. The report does not even take
in consideration that extraordinary fact and presents this meager result
as if it was a positive effect of having the mandatory automatic
inclusion in the registry.

We can safely affirm that, 4 years after the law, few people have
benefited from the automatic inclusion in the registry (the opt-out
regime) except the credit report agencies themselves.


### Risk of data breaches

One more reason to worry about sharing personal and financial data with
credit reporting agencies is the risk that that vast trove of data will
leak and end up in the hands of criminals.

This type of data broker has been reported in the news to be the
[suspected source](https://g1.globo.com/economia/tecnologia/noticia/2021/01/28/procon-sp-notifica-serasa-pedindo-explicacoes-sobre-vazamento-de-dados.ghtml)
of a
[2021 massive data breach of more than 223 million Brazilians](https://g1.globo.com/economia/tecnologia/noticia/2021/01/28/vazamento-de-dados-de-223-milhoes-de-brasileiros-o-que-se-sabe-e-o-que-falta-saber.ghtml).
The data includes name, CPF, date of birth, home address, phone, face
photo, educational degree, pension status, tax filings and credit score.
The number of people exceeds the total population of Brazil,
[accounted for as 203 million people in the official 2022 census](https://g1.globo.com/economia/censo/noticia/2023/06/28/censo-2022-brasil-tem-203-milhoes-de-habitantes-47-milhoes-a-menos-que-estimativa-do-ibge.ghtml),
because it reportedly also includes personal data on deceased people.

Civil society organizations that advocate for consumer protection, such
as IDEC, have
[raised serious concerns about the (Im)positive Registry and about millions of people having been put in risk of being targeted by criminals as a result of this data breach](https://idec.org.br/sites/default/files/vazamento_de_dados_200_milhoes.pdf).
The National Data Protection Agency (ANPD) declared, at the time, that
[they would be investigating the breach](https://www.gov.br/anpd/pt-br/assuntos/noticias/anpd-esta-apurando-no-caso-do-vazamento-de-dados-de-mais-de-220-milhoes-de-pessoas).
However, more than 2 years later, we have yet to see any consequence come
out as a result of that investigation.

The data brokers themselves have denied being the source of the data
breach. Some have even taken that opportunity to offer a paid service for
people to check with them whether or not their personal data has been
found on data breaches on the "dark web". The move is so ironic that one
could easily call them out for making themselves a poster child for the
term "privacy washing" – used to indicate when companies try to present
themselves to the public as privacy conscious, when in fact they do the
opposite in internal practice.


## How do I stop my data from being shared?

The only way to prevent your data on the SCR system from being shared
with the credit reporting agencies is to manifest your right to opt-out
of the (Im)positive Registry. That much is clear from Resolução CMN no.
5,037, Article 10, paragraph 2nd:

> It is forbidden to make available the information referred to in the
> caput about those registered who opt for the cancellation referred to in
> item I of article 5 of Law No. 12,414, of 2011.

[Cancellation can be done at any of the credit reporting agencies](https://tecnoblog.net/responde/como-sair-do-cadastro-positivo-cancelar-entrada/)
by online form, by phone, by mail (letter) or supposedly even in person
at some service points, depending on which agency you request. The caveat
is that whatever the requesting medium used, they'll likely try to get as
much personal information out of you as they can, with the excuse of
"identity verification", to make sure it is really you requesting
exclusion. The challenge lies in figuring out which one of them demands
providing fewer data in exchange.
