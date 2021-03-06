# Borax- python3 development util collections


[![PyPI](https://img.shields.io/pypi/v/borax.svg)](https://pypi.org/project/borax) 
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/borax.svg)](https://pypi.org/project/borax)
[![PyPI - Status](https://img.shields.io/pypi/status/borax.svg)](https://github.com/kinegratii/borax)




## Overview & Installation

Borax is a utils collections for python3 development, which contains some common data structures and the implementation of design patterns.

Use *pip* to install the package:

```shell
$ pip install borax

```

Or checkout source code:

```shell
git clone https://github.com/kinegratii/borax.git
cd borax
python setup.py install
```

## Modules Usage

### lunardate

> The dataset and algorithm is referenced from [jjonline/calendar.js](https://github.com/jjonline/calendar.js).

```python
from borax.calendars.lunardate import LunarDate

# Get the date instance of today.
print(LunarDate.today()) # LunarDate(2018, 7, 1, 0)

# Convert a solar date to the lunar date.
ld = LunarDate.from_solar_date(2018, 8, 11)
print(ld) # LunarDate(2018, 7, 1, 0)

# Return the lunar date after 10 days.

print(ld.after(10)) # LunarDate(2018, 7, 11, 0)
```

Return the lunar date after 10 days.

```
>>>ld.after(10)
LunarDate(2018, 7, 11, 0)
```

### Festivals

How many days away from spring festival,my birth day,Chinese New Year's Eve.

```python
from borax.calendars.festivals import get_festival, LunarSchema, DayLunarSchema

festival = get_festival('春节')
print(festival.countdown()) # 7

ls = LunarSchema(month=11, day=1)
print(ls.countdown()) # 285

dls = DayLunarSchema(month=12, day=1, reverse=1)
print(dls.countdown()) # 344
```

### Financial Capital Numbers

Convert amount to financial capital numbers.

```
>>> from borax.finance import financial_amount_capital
>>> financial_amount_capital(100000000)
'壹亿元整'
>>>financial_amount_capital(4578442.23)
'肆佰伍拾柒万捌仟肆佰肆拾贰元贰角叁分'
>>>financial_amount_capital(107000.53)
壹拾万柒仟元伍角叁分
```

### Singleton

```
>>>from borax.patterns.singleton import MetaSingleton
>>>class SingletonM(metaclass=MetaSingleton):pass
>>>a = SingletonM()
>>>b = SingletonM()
>>>id(a) == id(b)
True
```

### Fetch

A function sets for fetch the values of some axises.


Get list values from dict list.

```python
from borax.fetch import fetch

objects = [
    {'id': 282, 'name': 'Alice', 'age': 30},
    {'id': 217, 'name': 'Bob', 'age': 56},
    {'id': 328, 'name': 'Charlie', 'age': 56},
]

names = fetch(objects, 'name')
print(names)
```

Output

```
['Alice', 'Bob', 'Charlie']
```

## Document

See [online document](https://kinegratii.github.io/borax) for more detail, which is powered by [docsify](https://docsify.js.org/) .

## Development Features

- [x] [Typing Hints](https://www.python.org/dev/peps/pep-0484/)
- [x] [Flake8 Code Style](http://flake8.pycqa.org/en/latest/)
- [x] [nose](https://pypi.org/project/nose/)
- [x] [Travis CI](https://travis-ci.org)
- [x] [Docsify](https://docsify.js.org)

## License

This project is issued with MIT License, see LICENSE file for more detail.