---
layout: post
title: >-
  Aceptar bajo coacción no es consentimiento: cómo el Estado contribuye
  a someternos a las Big Tech
author: Augusto Herrmann
lang: es
ref: 2025-04-27-agreeing-under-coercion-is-not-consent-how-the-state-does-contribute-to-subjugate-us-to-big-tech
category: [es, blog]
tags: [datos personales, big tech, términos de servicio, aplicaciones]
cover: /assets/images/2025/04/cytonn-photography-GJao3ZTX9gU-unsplash.jpg
snippet-image: /assets/images/2025/04/cytonn-photography-GJao3ZTX9gU-unsplash.jpg
desc: >-
  Nos hemos acostumbrado a aceptar los términos de servicio sin leer, cediendo
  los datos y el poder a las pocas grandes empresas que controlan la internet.
  Lo peor de todo es que el poder estatal, en algunos países, especialmente
  en Brasil, ha contribuido a agravar esta situación, al condicionar el
  ejercicio de deberes y la efectivación de derechos a la aceptación por
  parte del ciudadano de las exigencias de las grandes plataformas. Sepa cómo
  podemos resistir y qué podemos hacer para intentar revertir esta situación.
image-credits: Cytonn Photography / Unsplash
---

{% assign posts=site.posts | where:"lang", page.lang | where: "ref", "2021-08-10-my-discord-with-discord-or-choosing-alternatives-with-better-terms-of-service" %}
{% for post in posts %}
{% assign reference_post=post %}
{% endfor %}

Desde hace muchos años, las personas han sido condicionadas a marcar la casilla
o hacer clic en el botón, sin leer, afirmando que aceptan los "términos de
servicio" y "política de privacidad" de todo servicio en línea que deseen
utilizar, sin reflexionar por un segundo sobre las consecuencias. El diablo
está en los detalles, ya que muchas veces, en las letras pequeñas, se esconden
prácticas de uso de datos personales que, de ser leídas, probablemente la
persona no aceptaría. Como, por ejemplo, el compartimiento de datos personales
con socios, para fines de marketing y otros fines no especificados.

Muchas veces, la persona no tiene la opción de no aceptar, por diversos motivos.
Por ejemplo, por presión social, considerando que todo su círculo social utiliza
el mismo aplicación de mensajería o red social. O incluso porque las empresas
con las que la persona necesita relacionarse solo utilizan un determinado
aplicativo de mensajería, sin el cual la relación de consumo se vuelve imposible.
En estos casos, la persona puede intentar buscar un competidor que utilice un
aplicativo diferente, pero no siempre es posible, ya que en la mayoría de las
veces todas las empresas utilizan el mismo aplicativo, siempre de las pocas
empresas llamadas
"[*Big Tech*](https://es.wikipedia.org/wiki/Gigantes_tecnol%C3%B3gicos)" que
detienen un monopolio u oligopolio del sector.

En el caso de Brasil, por ejemplo, se estableció un monopolio de facto de
WhatsApp, especialmente desde que la empresa Meta, dueña del aplicativo,
comenzó a pagar a los operadores de internet móvil por el privilegio de excluir
solo sus aplicativos de la franquicia de internet móvel, en detrimento de los
demás. En Brasil, los planes de internet móvil tienen limitaciones de volumen
de tráfico de datos. Si la persona utiliza cualquier otro aplicativo de
mensajería, como Signal o Element, pronto gastará su límite. Por otro lado,
si utiliza WhatsApp, no gasta nada. Es exactamente este desequilibrio de mercado
lo que llevó a la dominancia de este aplicativo en Brasil, donde casi el 100%
de las personas lo utilizan y se crea una expectativa social y comercial de
que todo el mundo necesita utilizarlo.

Esta distorsión del mercado llegó a ser evaluada entre 2015 y 2018 por
el [Consejo Administrativo de Defensa Económica - CADE](https://www.gov.br/cade/pt-br),
un organismo gubernamental cuyo objetivo es defender la competencia, que
decidió archivar el caso después de la declaración de la
[Anatel](https://www.gov.br/anatel/pt-br), con un argumento contrario a
cualquier lógica, de que la exención de cuota ampliaría la competencia y
estimularía la innovación. Diez años después, sabemos bien cuál fue el
resultado. Sin embargo, esta es una historia que contaré con más detalle
en otro texto. En esa ocasión, mostraré quiénes fueron las partes
involucradas, los argumentos y predicciones que hicieron y el contraste
con lo que realmente sucedió en los años siguientes. Una parte de la
historia ya la conté al Prof. Sérgio Amadeu en el
[episodio 92 del podcast Tecnopolítica](https://www.youtube.com/watch?v=gcJ7RnbMjE8).
Es un hecho indiscutible que, en estos años, se han ampliado enormemente
las situaciones que nos obligan, contra nuestra voluntad, a aceptar lo
que las "*Big Tech*" quieran imponernos.

<figure markdown="1">
![Imagen de un teléfono móvil sobre una mesa con una aplicación abierta.]({{ 'assets/images/2025/04/lana-codes-peHEZs9wFyM-unsplash.jpg' | relative_url }})
<figcaption>Las aplicaciones que no son subsidiadas por el oligopolio gastan la cuota de internet. Imagen: Lana Codes / Unsplash</figcaption>
</figure>

Sin embargo, la peor trampa es cuando el propio Estado establece
obligaciones, o impone condiciones para el ejercicio de derechos, a menos
que el ciudadano utilice determinada aplicación o red social de las "*Big
Tech*". Hoy vivimos la trágica situación en la que todas las aplicaciones
gubernamentales son de código cerrado, es decir, no se puede inspeccionar
el código fuente para verificar lo que realmente están haciendo y qué
datos están recopilando en su dispositivo.
[Cartera de Identidad Nacional - CIN](https://www.gov.br/governodigital/pt-br/identidade/identificacao-do-cidadao-e-carteira-de-identidade-nacional),
[Cartera Digital de Tránsito - CDT](https://www.gov.br/pt-br/apps/carteira-digital-de-transito-1)
(anteriormente llamada CNH Digital) y
[e-Título](https://www.justicaeleitoral.jus.br/titulo-eleitoral/) son
solo algunos ejemplos de aplicaciones gubernamentales, producidas
utilizando recursos públicos del erario, pero cuyo código fuente no es
accesible al público que pagó por ellas. Para saber más sobre por qué el
público debería tener derecho de acceso y uso al código fuente del
software por el que pagó, conozca la campaña
[*Public Money, Public Code*](https://publiccode.eu/es/) de la
[*Free Software Foundation Europe* - FSFE](https://fsfe.org/index.es.html). En
contraste con Brasil, muchas aplicaciones gubernamentales en países de la
Unión Europea, como Alemania, son de código abierto.

La falta de acceso al código fuente no es el único problema de estas
aplicaciones gubernamentales. Tal vez sea aún más grave el hecho de que
estas aplicaciones solo se pongan a disposición en las tiendas propiedad
de Google y Apple. Además del problema de la recopilación de datos de
todos los ciudadanos brasileños por parte de estas empresas extranjeras,
que es grave, también hay problemas legales y un problema de orden
democrático. Legalmente, no se puede establecer un contrato bajo coacción
o amenaza. Tal contrato no tiene validez legal. Además, el hecho de que
el ciudadano no pueda opinar o influir en los términos de servicio y las
políticas de privacidad se convierte en un problema de orden democrático
cuando todos se ven obligados por el Estado a aceptarlos.

Lo que el Estado está haciendo con esta práctica es privatizar la ley en
un proceso antidemocrático. El ciudadano tiene que obedecer y no tiene
ninguna participación en la definición del texto que supuestamente está
obligado a obedecer. Quienes determinan lo que aparece en estos términos
de servicio y políticas de privacidad son exclusivamente la propia
Alphabet, dueña de Google, y Apple. Lo que ellos escriben tiene fuerza de
ley y no hay nada que el ciudadano pueda hacer, ya que el Estado
condiciona el cumplimiento de deberes y el acceso a derechos a la
aceptación de estos términos. Es una tiranía de las *Big Tech*, con el aval
de los gobiernos de los países que adoptan la práctica de establecer
aplicaciones de código cerrado en tiendas propiedad de oligopolios
extranjeros como único medio de ejercer la ciudadanía.

En otros tiempos, la tiranía habría llevado a la revuelta popular contra
el tirano. En el caso presente, esto no ocurre, en gran parte, porque las
personas han sido condicionadas durante años por estas empresas del
oligopolio del Valle del Silicio a aceptar sin leer ni prestar atención a
las obligaciones y permisos "consentidos" en los términos de servicio. Con
esto, han logrado crear un sentimiento de resignación, en el que la gente
cree que todo está muy mal, pero cree que no hay nada que se pueda hacer.

<figure markdown="1">
![Foto de graffiti representando la resistencia por medio de puños cerrados y brazos levantados.]({{ 'assets/images/2025/04/jon-tyson-qn6mBa0twDY-unsplash.jpg' | relative_url }})
<figcaption>Imagen: Jon Tyson / Unsplash</figcaption>
</figure>

Esto no es cierto. Hay mucho que podemos hacer. No es fácil, pero hay
diversas actitudes que podemos tomar. Para empezar, exigir a los políticos
y votar a aquellos que se comprometan con políticas públicas que fomenten
la creación de infraestructura digital nacional. Por ejemplo, que
defiendan la idea de que si el software se desarrolla con recursos
públicos, pertenece al público y debe tener el código libre, como defiende
la campaña *Public Money, Public Code* de la FSFE. Exigir también que
valoren la protección de los datos personales y la soberanía digital,
fomentando el desarrollo de una infraestructura digital nacional, tanto en
términos de hardware
([nube soberana](https://www.nexojornal.com.br/expresso/2024/10/09/o-que-e-nuvem-soberana-e-por-que-o-brasil-quer-ter-uma)),
como en términos de software.

Además, es necesario desarrollar y retener los talentos formados en las
universidades brasileñas, para que los profesionales de tecnología
permanezcan en Brasil, en lugar de ir a trabajar en empresas extranjeras,
y para que el país tenga el dominio de la tecnología. Para ello, es
necesario que las universidades tengan una financiación adecuada para la
investigación y la enseñanza en el área de tecnología, en sentido contrario
a los recortes que se han realizado en los últimos años en nombre del
ajuste fiscal. Crear incentivos fiscales para que las empresas brasileñas
del sector se desarrollen, compensando el efecto fiscal con mayores
impuestos para las empresas extranjeras que ven al país como colonias
digitales para la extracción de datos.

Por otro lado, además de las cuestiones relacionadas con las políticas
públicas, también podemos tomar diversas actitudes a nivel personal. Usar
tiendas de aplicaciones libres, como [F-Droid](https://f-droid.org/) en
los dispositivos móviles basados en Android. Eliminar las aplicaciones
propietarias y que recopilan sus datos, incluyendo las que vienen
preinstaladas de fábrica - los llamados "*[bloatware](https://pt.wikipedia.org/wiki/Bloatware)*".
Hay guías y tutoriales en Internet que muestran paso a paso cómo hacer
esto. El foro [xdaforums.com](https://xdaforums.com/) suele tener guías
personalizadas para cada modelo de dispositivo móvil.

<figure markdown="1">
![Foto de un brazo con un guante sosteniendo un producto de limpieza.]({{ 'assets/images/2025/04/jeshoots-com-__ZMnefoI3k-unsplash.jpg' | relative_url }})
<figcaption>Imagen: JESHOOTS.COM / Unsplash</figcaption>
</figure>

Cada vez que te registres en un nuevo servicio, evalúa cuidadosamente qué
datos personales se están solicitando. Yo, como todo el mundo, no tengo
tiempo para leer con todos los detalles todos los términos de servicio de
todas las plataformas, sitios web, servicios y aplicaciones que necesito
usar. Por eso, es importante buscar el nombre del servicio, plataforma o
aplicación en [ToS;DR](https://tosdr.org/es), ver cuál es su calificación de
privacidad y los principales puntos negativos (o positivos) del resumen de
sus términos de servicio. Para entender qué es y cómo usar la herramienta,
lee [el texto que escribí sobre el tema]({{ reference_post.url | relative_url }}).

En el ámbito social y en las relaciones comerciales, prefiere siempre las
aplicaciones libres para el intercambio de mensajes, la navegación con
mapas y otras necesidades diarias. Presenta a las personas que conoces las
aplicaciones y soluciones utilizadas, para que vean que no solo ellas
reducen nuestra exposición de datos personales y sumisión a las empresas
del oligopolio extranjero de las "*Big Tech*". Tan importante como eso es
mostrar que estas soluciones también son viables, convenientes y fáciles
de usar en el día a día.
