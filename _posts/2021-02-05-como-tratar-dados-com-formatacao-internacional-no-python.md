---
layout: post
title: "Como tratar dados com formatação internacional no Python"
author: "Augusto Herrmann"
lang: pt
ref: 2021-02-05-how-to-deal-with-international-data-formats-in-python
category: [pt, blog]
tags: [
  python,ciência de dados,engenharia de dados,formatos,números,datas,
  moedas,internacional,substituir,locale,pontos,vírgulas,tutorial
]
cover: /assets/images/2021/02/jason-leung-tyler-easton-ZN2UhBtlrIY-unsplash.jpg
snippet-image: /assets/images/2021/02/jason-leung-tyler-easton-ZN2UhBtlrIY-unsplash.jpg
desc: >-
  Pontos ou vírgulas? Lidar com o os diferentes separadores decimais e
  formatos de datas pode parecer um inconveniente até que você se
  familiarize com o módulo locale do Python. Veja aqui como configurar
  e usar as localidades e interpretar números e datas.
image-credits: "Jason Leung & Tyler Easton / Unsplash"
---

Um inconveniente frequente ao tratar dados de diversas fontes
internacionais é como lidar com as diferenças entre as várias línguas e
culturas representam os seus separadores decimais e de milhares, a
ordem de ano, mês e dia nas datas, etc. Muitos países vão da menor (dia)
à maior (ano) unidade de tempo, enquanto que alguns, como os E.U.A.,
fazem a coisa estranha que é começar no meio (mês), então ir para o
menor (dia) e enfim inverter completamente a direção e ir para a maior
unidade (ano).

Se você olhar para os
[separadores decimais](https://pt.wikipedia.org/wiki/Separador_decimal),
parece que mais ou menos a metade do mundo usa pontos e a outra metade
usa vírgulas. O separador de milhares é o outro marcador. Isto é, em
países que usam o ponto como separador decimal, a vírgula é o dos
milhares e vice versa.

<figure markdown="1">
![Mapa mundi mostrando lugares por tipo de separador decimal]({{ 'assets/images/2021/02/decimal-separator-nuclear-vacuum.gif' | relative_url }})
<figcaption>Separador decimal em cada lugar:

<div class="legend">
  <span class="legend-color" style="background-color:#00b7ef; color:black;">
    &nbsp;
  </span>
  &nbsp;Ponto (.)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#a8e61d; color:black;">
    &nbsp;
  </span>
  &nbsp;Vírgula (,)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#54ce86; color:black;">
    &nbsp;
  </span>
  &nbsp;Ambos (pode variar dependendo do local ou outros fatores)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#ed1c24; color:black;">
    &nbsp;
  </span>
  &nbsp;Separador decimal arábico (٫)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#c0c0c0; color:black;">
    &nbsp;
  </span>
  &nbsp;Dados não disponíveis
</div>
Mapa feito por NuclearVacuum na Wikipedia</figcaption>
</figure>

## Interpretando números no Python, da maneira ingênua

O que as pessoas fazem frequentemente ao interpretar esses números com
Python é simplesmente usar o método `replace` da classe `str`.

```python
In [1]: number = '12,75'

In [2]: parsed = float(number.replace(',', '.'))

In [3]: parsed
Out[3]: 12.75
```

Mas e quando você também tem que levar em consideração os diferentes
separadores de milhares? E se você tiver um símbolo monetário antes ou
depois do número? As coisas ficam complicadas a ponto de deixar o
código pouco legível.

```python
In [1]: price = 'R$ 1.999,99'

In [2]: parsed = float(
   ...:     price
   ...:     .replace('R$', '')
   ...:     .strip()
   ...:     .replace('.', '')
   ...:     .replace(',', '.')
   ...: )

In [3]: parsed
Out[3]: 1999.99
```

Código assim também é frágil ao lidar com variabilidades na entrada.

## Interpretando datas no Python

Há situações em que você irá encontrar datas em fontes de dados que
estão formatadas em ordens diferentes, às vezes até com nomes de meses
e abreviaturas, como: `4-Feb-2021`. O Python vem com um módulo chamado
`datetime` na biblioteca padrão, que é bastante útil para lidar com
datas em praticamente qualquer formato que você seja capaz de encontrar:
simplesmente use o método `strptime` da classe `datetime`. Apenas veja a
[tabela de códigos de formatos](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)
e construa a sua máscara de formato. Aqui estão os códigos de formato
relevantes para o nosso exemplo:

| Diretiva | Significado | Exemplo |
| :-------- | :------ | :------ |
| %d | Dia do mês como um número decimal preenchido por zero. | 01, 02, …, 31 |
| %b | Mês como o nome abreviado da localidade. | Jan, Feb, …, Dec (en_US); <br /> Jan, Feb, …, Dez (de_DE) |
| %Y | Ano com o século, como um número decimal. | 0001, 0002, …, 2013, 2014, …, 9998, 9999 |

Note que a documentação diz que, ao usar o `strptime`, o preenchimento
de zeros no `%d` é opcional.

Então faça

```python
In [1]: from datetime import datetime

In [2]: written_date = '4-Feb-2021'

In [3]: parsed = datetime.strptime(written_date, '%d-%b-%Y').date()

In [4]: parsed
Out[4]: datetime.date(2021, 2, 4)
```

Essa abordagem também pode ser usada nos casos em que a ordem dos
componente da data é diferente. Apenas reordene a máscara de formato e
use o `strptime`.

Mas e se a data que você quer interpretar tem componentes em idiomas
diferentes (por exemplo, em português)? Você usa dicionários com os
nomes dos meses nessas línguas?

```python
french_months = {
  'janvier': 1,
  'février': 2,
  # meu Deus, por favor, não, pare! 😖 Arrête tout de suite ! 🤢
}
```

Por favor não faça isso.

## A solução apropriada, de fato

Tudo isso nos faz desejar que houvesse uma maneira padrão no Python de
lidar com todas essas diferenças em formatos de números e datas. E há!
Conheça o módulo `locale`. Ele também é
[parte da biblioteca padrão do Python](https://docs.python.org/3/library/locale.html),
mas é tão frequentemente ignorado em código que tenho visto nos meios de
ciência e engenharia de dados que me causa vergonha alheia ver coisas
como os exemplos deliberadamente ruins acima.

### Configurando as localidades

Antes de usar as localidades que você precisa no Python, todavia, você
precisa instalar essas localidades no seu sistema. O motivo para isso é
que o Python usa a base de dados de localidades do POSIX por trás dos
panos. A maneira de fazer isso varia, a depender do seu sistema
operacional e versão, mas se você está usando o Debian ou um sistema
baseado em Debian como o Ubuntu, então o seguinte deve funcionar.

1. Se já não tiver feito isso, instale o módulo `locales` no seu
   sistema.
   
   ```bash
   sudo apt-get install locales
   ```
2. Procure e edite o arquivo `/etc/locale.gen` no seu sistema. Isso
   provavelmente necessitará de privilégios de administrador. Encontre
   as localidades que você quer usar, descomente essas linhas e salve.

   Alternativamente, você pode usar o `sed` para
   [editar as linhas no próprio lugar](https://www.folkstalk.com/2012/02/sed-i-command-examples-in-unix-and.html),
   assim,

   ```bash
   sed -i 's/^# pt_BR.UTF-8 UTF-8$/pt_BR.UTF-8 UTF-8/g' /etc/locale.gen
   sed -i 's/^# fr_FR.UTF-8 UTF-8$/fr_FR.UTF-8 UTF-8/g' /etc/locale.gen
   ```

   for instance, to enable the German locale settings.
3. Rode o `locale-gen` para gerar as localidades que você escolheu. Por
   exemplo, se você quer ter disponíveis inglês dos E.U.A., francês e
   português do Brasil, você faria

   ```bash
   locale-gen en_US.UTF-8 fr_FR.UTF-8 pt_BR.UTF-8
   ```
4. Finalmente, atualize as localidades. Aqui você não precisa listar
   todas elas, apenas a padrão.
   
   ```bash
   update-locale LANG=pt_BR.UTF-8 LC_ALL=pt_BR.UTF-8
   ```

Você só precisa fazer essa configuração uma vez para cada vez que você
quiser adicionar ou remover uma localidade.

### Usando o módulo locale

Agora que o sistema tem as localidades que queremos usar, precismos
ajustá-las no Python antes de processar esses números.

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'pt_BR.UTF-8')
Out[1]: 'pt_BR.UTF-8'
```

Se estiver configurado corretamente, você não deve ver nenhum erro aqui.
Caso veja uma mensagem "**Error**: unsupported locale setting", ou
equivalente, volte e
[reconfigure as localidades](#configurando-as-localidades) e
certifique-se de ter habilitado aquela localidade.

Agora você pode trocar de localidades e tanto interpretar quanto
formatar números e datas da maneira apropriada para aquela localidade.
Você também pode trocar entre localidades sempre que necessário.

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'pt_BR.UTF-8')
Out[1]: 'pt_BR.UTF-8'

In [2]: locale.currency(0.5)
Out[2]: 'R$ 0,50'

In [3]: print('meia unidade: ' + locale.format_string('%.2f', 0.5))
meia unidade: 0,50

In [4]: locale.setlocale(locale.LC_ALL, 'en_US.UTF-8')
Out[4]: 'en_US.UTF-8'

In [5]: print('half a unit: ' + locale.format_string('%.2f', 0.5))
half a unit: 0.50
```

### Interpretando números em Python, da maneira apropriada

Para interpretar números de uma maneira que observe a localidade, o
módulo `locale` oferece as funções `atoi` (para inteiros) e `atof` (para
ponto flutuante).

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'pt_BR.UTF-8')
Out[1]: 'pt_BR.UTF-8'

In [2]: number = '12,75'

In [3]: parsed_number = locale.atof(number)

In [4]: parsed_number
Out[4]: 12.75

In [5]: price = 'R$ 1.999,99'

In [6]: parsed_price = locale.atof(price.split()[-1])

In [7]: parsed_price
Out[7]: 1999.99
```

A função `atof` também é muito útil para converter dados no Pandas, a
biblioteca ubíqua de ciência de dados em Python.

```python
In [1]: import pandas as pd

In [2]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'pt_BR.UTF-8')
Out[2]: 'pt_BR.UTF-8'

In [3]: df = pd.DataFrame(
   ...:       [
   ...:         ['banana', 'R$ 3,99'],
   ...:         ['maçã', 'R$ 4,49'],
   ...:         ['pêssego', 'R$ 8,90']
   ...:     ],
   ...:     columns=['fruta', 'preço'],
   ...: )

In [4]: df
Out[4]: 
     fruta    preço
0   banana  R$ 3,99
1     maçã  R$ 4,49
2  pêssego  R$ 8,90

In [5]: df['price'] = df['preço'].apply(lambda v: locale.atof(v.split()[-1]))

In [6]: df
Out[6]: 
     fruta    preço  price
0   banana  R$ 3,99   3.99
1     maçã  R$ 4,49   4.49
2  pêssego  R$ 8,90   8.90
```

### Interpretando datas

O módulo `datetime`, assim como toda a biblioteca padrão do Python,
observa o `locale`. Por isso, é fácil interpretar datas com os números
em ordem diferente ou com os nomes dos meses.

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'pt_BR.UTF-8')
Out[1]: 'pt_BR.UTF-8'

In [2]: from datetime import datetime

In [3]: written_date = '1-Mai-2021'

In [4]: parsed = datetime.strptime(written_date, '%d-%b-%Y').date()

In [5]: parsed
Out[5]: datetime.date(2021, 5, 1)
```

## Conclusão

Usar o módulo `locale` é uma habilidade essencial para muitas tarefas em
engenharia de dados e ciência de dados quando dados internacionais estão
envolvidos. Vale a pena adquirir prática com ele, já que o seu
processamento dos dados se tornará mais robusto e evitará erros comuns
ao fazer a limpeza dos dados.
