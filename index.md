## Elizabeth
[![Build Status](https://travis-ci.org/lk-geimfari/elizabeth.svg?branch=master)](https://travis-ci.org/lk-geimfari/elizabeth)
[![Documentation Status](https://readthedocs.org/projects/elizabeth/badge/?version=latest)](http://elizabeth.readthedocs.io/en/latest/?badge=latest)
[![PyPI version](https://badge.fury.io/py/elizabeth.svg)](https://badge.fury.io/py/elizabeth)
[![Python Version](https://img.shields.io/badge/python-v3.3%2C%20v3.4%2C%20v3.5%2C%20v3.6-brightgreen.svg)](https://github.com/lk-geimfari/elizabeth/)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/d773f20efa67430683bb24fff5af9db8)](https://www.codacy.com/app/likid-geimfari/church)


Elizabeth is a library to generate dummy data. It's very useful when you need to bootstrap your database. Elizabeth doesn't have any dependencies.

<p align="center">
  <img src="https://raw.githubusercontent.com/lk-geimfari/elizabeth/master/other/elizabeth_1.png">
  <br>
</p>



## Documentation
Elizabeth is a pretty simple library and all you need to start is the small documentation. See Elizabeth's Sphinx-generated documentation here: [http://elizabeth.readthedocs.io/en/latest/](http://elizabeth.readthedocs.io/en/latest/)

## Locales

At this moment a library has 15 supported locales:
 - da
 - de
 - en
 - es
 - fi
 - fr
 - is
 - it
 - nl
 - no
 - sv
 - ru
 - pt
 - pt-br
 - pl


## Installation
```zsh
➜  ~ pip install elizabeth
```

## Testing
```zsh
➜  ~ git clone https://github.com/lk-geimfari/elizabeth.git
➜  ~ cd elizabeth/
➜  ~ python3 -m unittest discover tests
```

## Examples

Below you can see, how to generate fake paths using `Elizabeth`:
```python
>>> from elizabeth import Path
>>> path = Path()

>>> path.root
'/'

>>> path.home
'/home/'

>>> path.user(gender='female')
'/home/chieko'

>>> path.users_folder(user_gender='male')
'/home/lyndon/Documents'

>>> path.dev_dir(user_gender='female')
'/home/edra/Development/Ruby'

>>> path.project_dir(user_gender='female')
'/home/katharina/Development/C Shell/litany'
```
or how to generate dummy model of transport:
```python
>>> from elizabeth import Transport
>>> transport = Transport()

>>> transport.truck()
'Union-0632 FX'

>>> transport.truck(model_mask="##/@")
'Jiaotong-78/P'

>>> transport.car()
'Pontiac Grand Am'

>>> transport.airplane()
'Boeing 575'

>>> transport.airplane(model_mask="7##")
'Airbus 778'
```

When you use only one locale you can use the `Generic` , that provides all providers at one class.

This is a contrived example, but it illustrates how this works.

```python
from elizabeth import Generic

el = Generic('en')


def patient(gender='female'):
    patient_card = {
        'full_name': el.personal.full_name(gender=gender),
        'gender': el.personal.gender(gender=gender),
        'blood_type': el.person.blood_type(),
        'birthday': el.datetime.birthday()
    }
return patient_card
```

## Data providers

| Provider        | Description                                                  |
| -------------   |:-------------                                                |
| Address         | *Address data (street name, street suffix etc.)*             |
| Business        | *Business data (company, company_type, copyright etc.)*      |
| Code            | *Codes (ISBN, EAN, IMEI etc.).*                              |
| ClothingSizes   | *Clothing sizes (international sizes, european etc.)*        |
| Datetime        | *Datetime (day_of_week, month, year etc.)*                   |
| Development     | *Data for developers (version, programming language etc.)*   |
| File            | *File data (extension etc.)*                                 |
| Food            | *Information on food (vegetables, fruits, measurements etc.)*|
| Personal        | *Personal data (name, surname, age, email etc.)*             |
| Text            | *Text data (sentence, title etc.)*                           |
| Transport       | *Dummy data about transport (truck model, car etc.)*         |
| Network         | *Network data (IPv4, IPv6, MAC address) etc*                 |
| Science         | *Scientific data (scientist, math_formula etc.)*             |
| Internet        | *Dummy internet data (facebook, twitter etc.)*                |
| Hardware        | *The data about the hardware (resolution, cpu, graphics etc.)*|
| Numbers         | *Numerical data (floats, primes, digit etc.)*                 |
| Path            | *Provides methods and property for generate paths.*           |
| Generic         | *All at one*                                                  |


## Contributing
Your contributions are always welcome! Please take a look at the [contribution](https://github.com/lk-geimfari/elizabeth/blob/master/CONTRIBUTING.md) guidelines first. [Here](https://github.com/lk-geimfari/elizabeth/blob/master/CONTRIBUTING.md) you can look a list of contributors


## Disclaimer
The author does not assume any responsibility for how you will use this library and how you will use data generated with this library. This library is designed only for developers and only with good intentions. Do not use the data generated with `Elizabeth` for illegal purposes.


## Licence
Elizabeth is licensed under the MIT License. See [LICENSE](https://github.com/lk-geimfari/elizabeth/blob/master/LICENSE)  for the full license text.