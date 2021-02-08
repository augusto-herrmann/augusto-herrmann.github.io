---
layout: post
title: "How to deal with international data formats in Python"
author: "Augusto Herrmann"
lang: en
ref: 2021-02-05-how-to-deal-with-international-data-formats-in-python
category: [en, blog]
tags: [
  python,data science,data engineering,formats,numbers,dates,currency,
  international,replace,locale,dots,commas,tutorial
]
cover: /assets/images/2021/02/jason-leung-tyler-easton-ZN2UhBtlrIY-unsplash.jpg
snippet-image: /assets/images/2021/02/jason-leung-tyler-easton-ZN2UhBtlrIY-unsplash.jpg
desc: >-
  Dots or commas? Handling the different decimal separators and date
  formats may seem like a hassle until you get acquainted with Python's
  locale module. Here is how you can configure and use locales to parse
  numbers and dates.
image-credits: "Jason Leung & Tyler Easton / Unsplash"
---

A frequent hassle when dealing with data from various international
sources is how to deal with differences in how various languages and
cultures represent decimal and thousands separators, the order of year,
month and day in dates, etc. Many countries go from the smaller (day)
to the largest (year) unit of time, while some, like the U.S., do the
weird thing that is starting from the middle (month), then going small
(day), then completely reversing direction going to the large unit
(year).

If you look at
[decimal separators](https://en.wikipedia.org/wiki/Decimal_separator),
it seems that just about half the world uses dots and the other half
uses commas. The thousands separator is the other mark. That is, in
countries that use the dot as decimal, the comma is the thousands
separator and vice versa.

<figure markdown="1">
![World map showing places by type of decimal separator]({{ 'assets/images/2021/02/decimal-separator-nuclear-vacuum.gif' | relative_url }})
<figcaption>Decimal separator by place:

<div class="legend">
  <span class="legend-color" style="background-color:#00b7ef; color:black;">
    &nbsp;
  </span>
  &nbsp;Dot (.)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#a8e61d; color:black;">
    &nbsp;
  </span>
  &nbsp;Comma (,)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#54ce86; color:black;">
    &nbsp;
  </span>
  &nbsp;Both (may vary by location or other factors)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#ed1c24; color:black;">
    &nbsp;
  </span>
  &nbsp;Arabic decimal separator (٫)
</div>
<div class="legend">
  <span class="legend-color" style="background-color:#c0c0c0; color:black;">
    &nbsp;
  </span>
  &nbsp;Data unavailable
</div>
Map by NuclearVacuum on Wikipedia</figcaption>
</figure>

## Parsing numbers in Python, the naïve way

What people often do when interpreting those numbers with Python is
simply using the `replace` method of the `str` class.

```python
In [1]: number = '12,75'

In [2]: parsed = float(number.replace(',', '.'))

In [3]: parsed
Out[3]: 12.75
```

But what about when you have also to take into account the different
thousands separators? What if you have a monetary symbol before or after
the number? Things get complicated then to the point of making the code
less readable.

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

Such code is also brittle when it comes to dealing with variabilities in
the input.

## Parsing dates in Python

There are times you will come across dates in data sources that are
formatted in different orders, sometimes even with month names and
abbreviations, like so: `4-Feb-2021`. Python comes with a `datetime`
module in the standard library which is quite useful for dealing with
dates in just about any format you can possibly find: just use the
`strptime` method of the `datetime` class. Just check the
[table of format codes](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)
and build your format mask. Here are the format codes relevant for our
example:

| Directive | Meaning | Example |
| :-------- | :------ | :------ |
| %d | Day of the month as a zero-padded decimal number. | 01, 02, …, 31 |
| %b | Month as locale’s abbreviated name. | Jan, Feb, …, Dec (en_US); <br /> Jan, Feb, …, Dez (de_DE) |
| %Y | Year with century as a decimal number. | 0001, 0002, …, 2013, 2014, …, 9998, 9999 |

Note that the documentation says that when using `strptime` the
zero-padding in `%d` is optional.

Then do

```python
In [1]: from datetime import datetime

In [2]: written_date = '4-Feb-2021'

In [3]: parsed = datetime.strptime(written_date, '%d-%b-%Y').date()

In [4]: parsed
Out[4]: datetime.date(2021, 2, 4)
```

That approach can also be used in cases where the order of the date
components is different. Just reorder the format mask and use
`strptime`.

But what if the date you need to parse has components in different
languages? Do you use dictionaries with the names of the months in
said languages?

```python
french_months = {
  'janvier': 1,
  'février': 2,
  # oh, God, please, no, stop! 😖 Arrête tout de suite ! 🤢
}
```

Please don't do that.

## The actual, proper solution

All of this makes us wish there was a standard way in Python to deal
with all those number and date format differences. And there is! Meet
the `locale` module. It is also
[part of the Python standard library](https://docs.python.org/3/library/locale.html),
but is so frequently ignored in code I have seen in data science and
data engineering circles that it makes me cringe when I see things like
some of the deliberately bad code examples above.

### Configuring locales

Before you can use the locales you need in Python, however, you need to
install those locales in your system. The reason for that is that Python
uses the POSIX locale database upstream. The way to do it varies
depending on your operating system and version, but if you're using
Debian or a Debian based system like Ubuntu, then the following should
work.

1. If you haven't already, install the `locales` module on your system.
   
   ```bash
   sudo apt-get install locales
   ```
2. Locate and edit the `/etc/locale.gen` file on your system. That will
   probably require administrator privileges. Find the locales you want
   to use, uncomment those lines and save.

   Alternatively, you can use `sed` to
   [edit the lines in-place](https://www.folkstalk.com/2012/02/sed-i-command-examples-in-unix-and.html),
   like this,

   ```bash
   sed -i 's/^# de_DE.UTF-8 UTF-8$/de_DE.UTF-8 UTF-8/g' /etc/locale.gen
   sed -i 's/^# fr_FR.UTF-8 UTF-8$/fr_FR.UTF-8 UTF-8/g' /etc/locale.gen
   ```

   for instance, to enable the French and German locale settings.
3. Run `locale-gen` to generate the locales you have chosen. For
   example, if you wish to have U.S. English, German and French enabled,
   you would do

   ```bash
   locale-gen en_US.UTF-8 de_DE.UTF-8 fr_FR.UTF-8
   ```
4. Finally, update the locales. Here you don't need to list them all,
   just the default one.
   
   ```bash
   update-locale LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8
   ```

You just need to do this configuration once for every time you wish to
add or remove a locale.

### Using the locale module

Now that the system has the locales we want to use, we need to set them
in Python before we process those numbers.

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'de_DE.UTF-8')
Out[1]: 'de_DE.UTF-8'
```

If it is properly configured, you should see no errors here. If you see
an "**Error**: unsupported locale setting" message, go back and
[reconfigure the locales](#configuring-locales) and make sure you have
that locale enabled.

Now you can switch locales and both parse and format numbers and dates
in the proper way for that locale. You can also switch between locales
when needed.

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'de_DE.UTF-8')
Out[1]: 'de_DE.UTF-8'

In [2]: locale.currency(0.5)
Out[2]: '0,50 €'

In [3]: print('eine halbe Einheit: ' + locale.format_string('%.2f', 0.5))
eine halbe Einheit: 0,50

In [4]: locale.setlocale(locale.LC_ALL, 'en_US.UTF-8')
Out[4]: 'en_US.UTF-8'

In [5]: print('half a unit: ' + locale.format_string('%.2f', 0.5))
half a unit: 0.50
```

### Parsing numbers in Python, the proper way

For interpreting numbers in a locale aware way, the `locale` module
provides the `atoi` (for integers) and `atof` (for floats) functions.

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

The `atof` function is also very useful for converting data in Pandas,
the ubiquitous data science library in Python.

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

### Parsing dates

The `datetime` module, as with all of the Python standard libraries, is
`locale` aware. So, parsing dates with a different order of numbers or
with month names is easy.

```python
In [1]: import locale
   ...: locale.setlocale(locale.LC_ALL, 'de_DE.UTF-8')
Out[1]: 'de_DE.UTF-8'

In [2]: from datetime import datetime

In [3]: written_date = '1-Mai-2021'

In [4]: parsed = datetime.strptime(written_date, '%d-%b-%Y').date()

In [5]: parsed
Out[5]: datetime.date(2021, 5, 1)
```

## Conclusion

Using the `locale` module is an essential ability for many data
engineering and data science tasks when you have international data
involved. It pays off to have some practice with it as your data
processing will be more robust and avoid common mistakes when cleaning
data.
