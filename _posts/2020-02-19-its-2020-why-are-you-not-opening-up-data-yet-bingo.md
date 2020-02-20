---
layout: post
title: "It's 2020. Why are you not opening up data yet? Bingo!"
author: "Augusto Herrmann"
lang: en
ref: 2020-02-19-its-2020-why-are-you-not-opening-up-data-yet-bingo
category: [en, blog]
tags: [open data, data publisher]
cover: /assets/images/2020/02/sydney-rae-geM5lzDj4Iw-unsplash.jpg
desc: >-
  A new year has arrived and some people are still using old excuses not to
  open up data that should be available for the public to use. How could we
  address those concerns and defuse some objections people still might have?
image-credits: "sydney Rae / Unsplash"
---

When I started advocating for and building open data eleven years ago, the
world was a very different place. Brazil had neither open data portal nor
policy, and even the countries that pioneered the open data agenda were
just beginning.

Now we can see a very different landscape. Most nation states have
[joined the open data agenda](https://opendatacharter.net/) and feature a one
stop shop portal where people can download a plethora of data about almost
any subject, including
[the most important ones](https://index.okfn.org/place/). Many local
governments do so, too.

It may seem so that public sector managers have been since then mostly
convinced already of the
[reasons](https://opendatahandbook.org/guide/en/why-open-data/)
[for](https://okfn.org/opendata/why-open-data/)
[opening](https://theodi.org/article/what-is-open-data-and-why-should-we-care/)
[up](https://kit.dados.gov.br/vantagens-dados-abertos/)
[data](https://www.europeandataportal.eu/en/using-data/benefits-of-open-data),
be they for economic growth, job creation, public sector cost savings and
efficiency, improvement of public and private services, a smarter way of
addressing social challenges, improving government transparency and
accountability, or even unforeseen positive effects.

<figure markdown="1">
![Diagram on the benefits of open data, from the European Data Portal]({{ 'assets/images/2020/02/advantages-of-open-data.png' | relative_url }})
<figcaption>Diagram on the benefits of open data, from the <a href="https://www.europeandataportal.eu/en/using-data/benefits-of-open-data" target="_blank">European Data Portal</a>.</figcaption>
</figure>

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2019-11-25-on-the-state-of-open-data-does-it-face-an-identity-crisis" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

However, as surveys such as the
[Open Data Index](https://index.okfn.org/place/),
[Open Data Barometer](https://opendatabarometer.org/?_year=2017&indicator=ODB)
and
[Open Data Inventory](https://odin.opendatawatch.com/report/rankings) have
shown, there are still many gaps in important and potentially useful data that
should be available, but isn't. We're still a long way from living in an open
data utopia. For more on this point, please see my previous post
“[{{ reference_post.title }}]({{ reference_post.url | relative_url }})”.

The reality is that open data has not really taken off with politicians.
Rarely does one acknowledge the existence of the agenda, let alone set it as
a political priority for economic development. That is despite the fact that,
the more open data is available, the more it enables the private sector to
leverage emerging artificial intelligence applications and innovate in
products and services.

However, for people who work in the public sector and for people who often
try to get data from governments by using access to information laws, it is
often the case that access to data will be denied or hindered by managers
using the same old excuses that we have been getting for many years.

## The Open Data Bingo

A set of numbers that you sit while waiting for each one to be announced.
Bingo! This is probably what has inspired the name of
[the original Open Data Bingo](http://data.dev8d.org/devbingo/bingo.php?n=1&w=4&h=4&title=%22Open+Data+Excuse%22+Bingo&tag=%23openDataExcuses&statements=Terrorists+will+use+it%0D%0AData+Protection%0D%0ALawyers+want+a+custom+License%0D%0APoor+Quality%0D%0AThieves+will+use+it%0D%0AWe%27ll+get+spam%0D%0AIt%27s+not+very+interesting%0D%0AIt%27s+too+complicated%0D%0AThere%27s+no+API%0D%0AWhat+if+we+want+to+sell+it+later%0D%0AI+don%27t+mind%2C+but+someone+else+might%0D%0AIt%27s+too+big%0D%0AThere%27s+already+a+project+to...%0D%0APeople+may+misinterpret+the+data%0D%0AWe+might+want+to+use+it+in+a+paper%0D%0AWe+will+get+too+many+enquiries&rules=%3Cp%3EFor+open+data+teams%3B+print+out+a+copy+and+put+it+on+your+office+wall.+Cross+out+each+excuse+people+give+you.+There+are+no+prizes%2C+but+you+can+tweet+%22bingo!+%23openDataExcuses%22+if+you+think+it+might+make+you+feel+better*.%3C%2Fp%3E%0D%0A%0D%0A%3Cp+style%3D%27font-size%3A80%25%27%3E*+it+won%27t%3C%2Fp%3E).
It's just a chart of the most common excuses people give for not opening up
data. Then, it was improved upon by a few people, among them Christopher
Gutteridge (University of Southampton) and Alexander Dutton (University of
Oxford), by collaborating on a
[Google Docs document](https://docs.google.com/document/d/1nDtHpnIDTY_G32EMJniXaOGBufjHCCk4VC9WGOf7jK4/edit#heading=h.kuxx5ny497m9).
It then took the Italian group
[Spaghetti Open Data](http://www.spaghettiopendata.org/), and
[Francesco Minazzi](https://twitter.com/digitjus) in particular, to adapt
the Bingo to the Italian open data landscape and produce a website:
“[Il bingo delle scuse](http://gbonanome.github.io/opendatabingo/about.html)”.

<figure markdown="1">
![The Italian Open Data Bingo]({{ 'assets/images/2020/02/italian-open-data-bingo.gif' | relative_url }})
<figcaption>The Italian Open Data Bingo</figcaption>
</figure>

Some time later, open data activist and current Director of the
[Open Knowledge Foundation chapter in Brazil](https://br.okfn.org/),
[Fernanda Campagnucci](http://umdadoamais.com/), translated some of the content
and adapted it to the Brazilian reality, drawing upon her own experience in
opening up data in the local administration of the city of São Paulo. She
put up [a website](https://campagnucci.github.io/opendatabingo/) online with
this version. She then mentioned it while being a guest in an episode of the
[Pizza de Dados Podcast](http://umdadoamais.com/dados-do-ponto-de-vista-do-governo-pizza-de-dados/),
and that's how I first heard of the open data bingo.

When considering the arguments for the adaptation of this content for many
different countries and cultures, it is remarkable how similar the barriers
for opening up data are among them.

## bingo.dadosabertos.social

I then finished the translation and adaptation to the Brazilian context of the
rest of the questions that were still in Italian, and gave it a fancy domain
name. Hence, [bingo.dadosabertos.social](https://bingo.dadosabertos.social/).
I hope this helps the Brazilian open data community argue more effectively to
obtain data from public administrations. Let's then try to fill those gaps in
important data that should be, but is not yet open!

Just as this project did not start with me, it should not finish here.
It is completely open licensed and
[available on Github](https://github.com/augusto-herrmann/opendatabingo).
So fork it, create your version, and send me a pull request if you know
Portuguese and has an useful argument against the excuses not to open up data.
If you're not familiar with Github, you can leave your comment on the
[dadosabertos.social forum](https://dadosabertos.social/t/e-2020-por-que-voce-ainda-nao-esta-abrindo-dados-bingo/213)
as well. If you know the context of Brazilian laws, institutions and data
landscape, all the better! Your contributions will be most welcome.

