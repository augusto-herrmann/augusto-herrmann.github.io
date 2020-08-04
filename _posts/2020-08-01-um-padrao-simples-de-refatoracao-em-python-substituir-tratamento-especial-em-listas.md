---
layout: post
title: >-
  Um padrão simples de refatoração em Python: substituir tratamento especial
  em listas
author: "Augusto Herrmann"
lang: pt
ref: 2020-08-01-a-simple-python-refactoring-pattern-replacing-special-handling-in-lists
category: [pt, blog]
tags: [python, code refactoring]
cover: /assets/images/2020/08/ant-rozetsky-SLIFI67jv5k-unsplash.jpg
desc: >-
  Uma maneira de refatorar código Python quando você tem que lidar de uma
  maneira consistente com alguns casos especiais em uma lista.
image-credits: "Ant Rozetsky / Unsplash"
---

Quando nos descobrimos a repetir o mesmo código ou similar em vários lugares
nos nossos arquivos, sabemos que é hora de refatorá-lo. Caso contrário ele se
torna difícil de manter a longo prazo e acumula dívida técnica.

se você perceber um monte de `if`s espalhados pelo código para tratar casos
especiais, dependendo dos valores dos itens de uma lista, então uma possível
refatoração simples poderia ser assim.

Só para tomar um exemplo, suponha que você tenha uma lista de itens. Por
exemplo, uma lista de cidades ao redor do mundo. Elas poderiam ser possíveis
destinos para onde você poderia enviar alguns produtos.

```python
In [1]: cidades = [
            'Manaus',
            'Belém',
            'Recife',
            'Maceió',
            'Salvador',
            'Belo Horizonte',
            'Brasília',
            'Rio de Janeiro',
            'São Paulo',
            'Porto Alegre',
            'Berlim',
            'Cidade do Cabo',
            'Bangalore',
            'Melbourne'
        ]
```

Então, suponha que em vários lugares do seu código você tem que dar algum tipo
de tratamento especial para alguns dos itens dessa lista. Imagine que, se você
estiver enviando produtos comprados, caso a cidade de destino seja no exterior
você terá que direcioná-los a um *workflow* diferente para prepará-los para a
exportação.

```python
In [2]: for cidade in cidades:
            if cidade in ['Berlim', 'Cidade do Cabo', 'Bangalore', 'Melbourne']:
                print ('enviar para exportação')
            else:
                print (f'enviar para {cidade}')
```
```
enviar para Manaus
enviar para Belém
enviar para Recife
enviar para Maceió
enviar para Salvador
enviar para Belo Horizonte
enviar para Brasília
enviar para Rio de Janeiro
enviar para São Paulo
enviar para Porto Alegre
enviar para exportação
enviar para exportação
enviar para exportação
enviar para exportação
```

Caso você faça isso apenas uma vez, não é um problema. Mas se os casos
especiais tiverem que ser tratados em mais de um lugar, o código se torna
difícil de manter. Sempre que você mudar ou adicionar uma exceção entre os
itens que precisam ser tratados de forma diferente, você teria que manter
essa mudança em vários lugares e correr o risco de esquecer um lugar, o
que levaria a possíveis erros.

Vamos criar uma função para arrumar esse código. Sempre que precisarmos usar
os casos especiais, simplesmente usaremos essa função.

```python
In [3]: def get_destino_envio(lugar: str):
            lugares_envio = {
                'Berlim': 'exportação',
                'Cidade do Cabo': 'exportação',
                'Bangalore': 'exportação',
                'Melbourne': 'exportação'
            }
            return lugares_envio.get(lugar, lugar)
```

Aqui estamos usando o método `get` presente em dicionários padrão do Python.
O seu primeiro argumento é a chave a ser procurada no dicionário. O segundo é
o *default* a retornar quando não se encontra a chave.

Agora, substitua por uma chamada a essa função todas as instâncias de código
em que você costumava verificar por casos especiais na lista:

```python
In [4]: for cidade in cidades:
            print (f'enviar para {get_destino_envio(cidade)}')
```
```
enviar para Manaus
enviar para Belém
enviar para Recife
enviar para Maceió
enviar para Salvador
enviar para Belo Horizonte
enviar para Brasília
enviar para Rio de Janeiro
enviar para São Paulo
enviar para Porto Alegre
enviar para exportação
enviar para exportação
enviar para exportação
enviar para exportação
```

Agora, sempre que o conjunto de casos especiais precisar de manutenção, você
só precisa alterar as coisas em um lugar.

Você também pode usar a função em um `map` para transformar a lista, se
precisar:

```python
In [5]: print('\n'.join(map(get_destino_envio, cidades)))
```
```
para Manaus
para Belém
para Recife
para Maceió
para Salvador
para Belo Horizonte
para Brasília
para Rio de Janeiro
para São Paulo
para Porto Alegre
para exportação
para exportação
para exportação
para exportação
```

E se você estiver usando Pandas, você pode, é claro, também aplicá-la com
`apply` a uma coluna para transformá-la:

```python
In [6]: import pandas as pd

        df = pd.DataFrame(cidades, columns=['cidade'])

        df['destino'] = df.cidade.apply(get_destino_envio)

        df
```

|   | cidade | destino |
|   | ---- | ----------- |
| 0 | Manaus | para Manaus |
| 1 | Belém | para Belém |
| 2 | Recife | para Recife |
| 3 | Maceió | para Maceió |
| 4 | Salvador | para Salvador |
| 5 | Belo Horizonte | para Belo Horizonte |
| 6 | Brasília | para Brasília |
| 7 | Rio de Janeiro | para Rio de Janeiro |
| 8 | São Paulo | para São Paulo |
| 9 | Porto Alegre | para Porto Alegre |
| 10 | Berlim | para exportação |
| 11 | Cidade do Cabo | para exportação |
| 12 | Bangalore | para exportação |
| 13 | Melbourne | para exportação |

Usar padrões ao refatorar código pode nos economizar tempo ao melhorar a
manutenabilidade e legibilidade do código. Este padrão simples foi algo que
eu encontrei ao refatorar um código do mundo real, apesar das especificidades
serem bastante diferentes deste exemplo fictício. E escrever sobre isso me
permite não apenas organizar meus pensamentos e compartilhar a experiência
com outros, mas também internalizar as decisões sobre como estruturar código.

