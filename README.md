[![](https://img.shields.io/pypi/v/calendra.svg)][1]

[![](https://img.shields.io/pypi/pyversions/calendra.svg)][1]

  [1]: https://pypi.org/project/calendra

[![Automated Tests](https://github.com/jaraco/calendra/workflows/Automated%20Tests/badge.svg)](https://github.com/jaraco/calendra/actions?query=workflow%3A%22Automated+Tests%22)

[![](https://readthedocs.org/projects/calendra/badge/?version=latest)](https://calendra.readthedocs.io/en/latest/?badge=latest)

## Overview

Calendra is a Python module that offers classes able to handle calendars, list legal / religious holidays and gives working-day-related computation functions.

## History

Calendra is a fork of [Workalendar](https://github.com/peopledoc/workalendar)
designed to be more extensible and introspectable, adding interfaces where
[Workalendar is philosophically opposed for the sake of simplicity](https://github.com/peopledoc/workalendar/pull/79).

What can Calendra do that Workalendar cannot?

- Provides descriptions for holidays for the "day indicated" for each
  Holiday (such as '3rd Monday in August').
- Keeps distinct the indicated and observed dates for Holidays, such
  that it's possible to determine on what day a given holiday is observed.
- Allows the number of Holidays in a calendar year to be counted.
- Consolidates observance logic in the core code rather than requiring
  each calendar implementation to implement its own.

## Status

The project is stable and in production use. Calendra follows the principles of [semver](https://semver.org) for released verisons.

If you spot any bug or wish to add a calendar, please refer to the [Contributing doc](https://peopledoc.github.io/workalendar/contributing.html).

## Usage sample

```python-repl
>>> from datetime import date
>>> from calendra.europe import France
>>> cal = France()
>>> cal.holidays(2012)
[(datetime.date(2012, 1, 1), 'New year'),
 (datetime.date(2012, 4, 9), 'Easter Monday'),
 (datetime.date(2012, 5, 1), 'Labour Day'),
 (datetime.date(2012, 5, 8), 'Victory in Europe Day'),
 (datetime.date(2012, 5, 17), 'Ascension Day'),
 (datetime.date(2012, 5, 28), 'Whit Monday'),
 (datetime.date(2012, 7, 14), 'Bastille Day'),
 (datetime.date(2012, 8, 15), 'Assumption of Mary to Heaven'),
 (datetime.date(2012, 11, 1), "All Saints' Day"),
 (datetime.date(2012, 11, 11), 'Armistice Day'),
 (datetime.date(2012, 12, 25), 'Christmas')]
>>> cal.is_working_day(date(2012, 12, 25))  # it's Christmas
False
>>> cal.is_working_day(date(2012, 12, 30))  # it's Sunday
False
>>> cal.is_working_day(date(2012, 12, 26))
True
>>> cal.add_working_days(date(2012, 12, 23), 5)  # 5 working days after Xmas
datetime.date(2012, 12, 31)
```

For a more complete documentation and advanced usage, go to [the official workalendar documentation](https://peopledoc.github.io/workalendar).

## External dependencies

Calendra has been tested on the Python versions declared in setup.cfg.

If you're using wheels, you should be fine without having to install extra system packages. As of `v7.0.0`, we have dropped `ephem` as a dependency for computing astronomical ephemeris in favor of `skyfield`. So if you had any trouble because of this new dependency, during the installation or at runtime, [do not hesitate to file an issue](https://github.com/peopledoc/workalendar/issues/).

## Tests

To run test, just install tox with `pip install tox` and run `tox`
from the command line.


## Available Calendars

### Europe

- Austria
- Belarus
- Belgium
- Bulgaria
- Cayman Islands
- Croatia
- Cyprus
- Czech Republic
- Denmark
- Estonia
- European Central Bank
- Finland
- France
- France (Alsace / Moselle)
- Germany
- Greece
- Hungary
- Iceland
- Ireland
- Italy
- Latvia
- Lithuania
- Luxembourg
- Malta
- Monaco
- Netherlands (optionally with school holidays and carnival)
- Norway
- Poland
- Portugal
- Romania
- Russia
- Serbia
- Slovakia
- Slovenia
- Spain (Andalusia, Aragon, Castile and León, Castilla-La Mancha, Canary Islands, Extremadura, Galicia, Balearic Islands, La Rioja, Community of Madrid, Murcia, Navarre, Asturias, Basque Country, Cantabria, Valencian Community)
- Sweden
- Switzerland (Aargau, Appenzell Innerrhoden, Appenzell Ausserrhoden, Bern, Basel-Landschaft, Basel-Stadt, Fribourg, Geneva, Glarus, Graubünden, Jura, Luzern, Neuchâtel, Nidwalden, Obwalden, St. Gallen, Schaffhausen, Solothurn, Schwyz, Thurgau, Ticino, Uri, Vaud, Valais, Zug, Zurich)
- Turkey
- Ukraine
- United Kingdom (incl. Northern Ireland, Scotland and all its territories)

### America

- Argentina
- Barbados
- Brazil (all states, cities and for bank transactions, except the city of Viana)
- Canada (including provincial and territory holidays)
- Chile
- Colombia
- Mexico
- Panama
- Paraguay
- United States of America
  - State holidays for all the 50 States
  - American Samoa
  - Chicago, Illinois
  - Guam
  - Suffolk County, Massachusetts
  - California Education, Berkeley, San Francisco, West Hollywood
  - Florida Legal and Florida Circuit Courts, Miami-Dade

### Asia

- China
- Hong Kong
- Israel
- Japan
- JapanBank
- Malaysia
- Qatar
- Singapore
- South Korea
- Taiwan

### Oceania

- Australia (incl. its different states)
- Marshall Islands
- New Zealand

### Africa

- Algeria
- Angola
- Benin
- Ivory Coast
- Kenya
- Madagascar
- Mozambique
- São Tomé
- South Africa

And more to come (I hope!)

## Caveats

Please take note that some calendars are not 100% accurate. The most common example is the Islamic calendar, where some computed holidays are not exactly on the same official day decided by religious authorities, and this may vary country by country. Whenever it's possible, try to adjust your results with the official data provided by the adequate authorities.


## Contributing

Please read our [contributing.md](https://github.com/peopledoc/workalendar/blob/master/docs/contributing.md) document to discover how you can contribute to `workalendar`. Pull-requests are very welcome.

## License

This library is published under the terms of the MIT License. Please check the LICENSE file for more details.
