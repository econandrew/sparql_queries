# Big list of country aliases (~50k rows)

I needed a big list of country aliases and I couldn't find one. The R package
[`countrycode`](https://github.com/vincentarelbundock/countrycode) does a good job of converting country names to a standard form,
but it uses regular expressions so it's not much use to _generate_ country aliases. This list is created using the SPARQL query shown,
which can be run against http://query.wikidata.org. It extracts country names from wikidata. The output is in the CSV file.

The fields are:
- `iso3c` - ISO 3166-1 alpha-3 code
- `iso2c` - ISO 3166-1 alpha-2 code
- `language` - ISO language code for the label
- `is_official_language` - 'true', if that language is listed as an official language of the country
- `label` - the (unicode) label for that country
- `label_type` - either 'official' if this is listed as a primary label in wikidata, or 'alias' if it's listed as "Also known as".

Note label_type == 'alias' gets pretty colloqiual, e.g. for the United States of America in English:
- USA
- America
- the States
- U.S.
- U.S.A.
- US
- 🇺🇸
- the US
- United States

There are definitely issues, so raise them and I'll try to fix!
