## Outils pour travailler avec les DECP

#### Import des données JSON

- initialement `jsonlite::fromJSON()`
- si ***"Erreur : lexical error: invalid char in json text."*** --> `RJSONIO::fromJSON(x, nullValue = NA)`


#### Comparer des JSON

- package [bergant/jsondiff](https://github.com/bergant/jsondiff), fonction `jsondiff::jsondiff(json1, json2)`
