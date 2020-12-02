---
layout: post
title: >-
  A simple Python code refactoring pattern: replacing special handling in
  lists
author: "Augusto Herrmann"
lang: en
ref: 2020-08-01-a-simple-python-refactoring-pattern-replacing-special-handling-in-lists
category: [en, blog]
tags: [python, code refactoring, how to]
cover: /assets/images/2020/08/ant-rozetsky-SLIFI67jv5k-unsplash.jpg
snippet-image: /assets/images/2020/08/ant-rozetsky-SLIFI67jv5k-unsplash.jpg
desc: >-
  A way to refactor Python code when you have to handle in a consistent way
  just a few special cases on a list.
image-credits: "Ant Rozetsky / Unsplash"
---

Whenever we find ourselves repeating the same or similar code in several
places around our files, we know it's time for refactoring it. Otherwise
it becomes difficult to maintain in the long run and accumulates technical
debt.

If you spot a bunch of `if`s around the code for handling special cases,
depending on the values of items in a list, then one possible simple code
refactoring could go like this.

Just to take a simple example, suppose you have a list of items. For
instance, a list of cities around the world. These could be the possible
destinations where you would ship some products to.

```python
In [1]: cities = [
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
            'Berlin',
            'Cape Town',
            'Bangalore',
            'Melbourne'
        ]
```

Then, suppose that on several places around your code you have to give some
form of special treatment for some of the items in that list. Imagine that,
if you're shipping purchased products, if the destination city is abroad you
have to direct them to a different workflow to prepare them for export.

```python
In [2]: for city in cities:
            if city in ['Berlin', 'Cape Town', 'Bangalore', 'Melbourne']:
                print ('ship it for export')
            else:
                print (f'ship it to {city}')
```
```
ship it to Manaus
ship it to Belém
ship it to Recife
ship it to Maceió
ship it to Salvador
ship it to Belo Horizonte
ship it to Brasília
ship it to Rio de Janeiro
ship it to São Paulo
ship it to Porto Alegre
ship it for export
ship it for export
ship it for export
ship it for export
```

In case you do this just once, it's no big deal. But if the special cases have
to be handled in more than one place, the code becomes difficult to maintain.
Whenever you change or add an exception among the items that have to be
handled differently, you would have to maintain this change in several places,
and risk forgetting one place, which would lead to possible errors.

Let's create a function to wrap this code up. Whenever we need to use the
special cases, we just use that function.

```python
In [3]: def get_shipping_destination(place: str):
            shipping_places = {
                'Berlin': 'for export',
                'Cape Town': 'for export',
                'Bangalore': 'for export',
                'Melbourne': 'for export'
            }
            return shipping_places.get(place, 'to ' + place)
```

Here we're using the method `get` present in standard Python dictionaries.
Its first argument is the key to look for in the dictionary. The second is
the default to return when you don't find the key.

Now, replace with a call to that function all of the instances of code where
you used to check for the special cases in the list:

```python
In [4]: for city in cities:
            print (f'ship it {get_shipping_destination(city)}')
```
```
ship it to Manaus
ship it to Belém
ship it to Recife
ship it to Maceió
ship it to Salvador
ship it to Belo Horizonte
ship it to Brasília
ship it to Rio de Janeiro
ship it to São Paulo
ship it to Porto Alegre
ship it for export
ship it for export
ship it for export
ship it for export
```

Now, whenever the set of special cases needs maintenance, you only need to
change things in one place.

You can also use the function on a `map` to transform the list if you need it:

```python
In [5]: print('\n'.join(map(get_shipping_destination, cities)))
```
```
to Manaus
to Belém
to Recife
to Maceió
to Salvador
to Belo Horizonte
to Brasília
to Rio de Janeiro
to São Paulo
to Porto Alegre
for export
for export
for export
for export
```

And if you're using Pandas, you can of course also `apply` it to a column
to transform it:

```python
In [6]: import pandas as pd

        df = pd.DataFrame(cities, columns=['city'])

        df['destination'] = df.city.apply(get_shipping_destination)

        df
```

|   | city | destination |
|   | ---- | ----------- |
| 0 | Manaus | to Manaus |
| 1 | Belém | to Belém |
| 2 | Recife | to Recife |
| 3 | Maceió | to Maceió |
| 4 | Salvador | to Salvador |
| 5 | Belo Horizonte | to Belo Horizonte |
| 6 | Brasília | to Brasília |
| 7 | Rio de Janeiro | to Rio de Janeiro |
| 8 | São Paulo | to São Paulo |
| 9 | Porto Alegre | to Porto Alegre |
| 10 | Berlin | for export |
| 11 | Cape Town | for export |
| 12 | Bangalore | for export |
| 13 | Melbourne | for export |

Using patterns when refactoring code can save us time by improving code
maintainability and readability. This simple pattern was something I
came across while refactoring some real world code, even though the
specifics are quite different from this fictional example. And writing
about it lets me to not only organize my thoughts and share the
experience with others, but also to internalize decisions on how to
structure code.

