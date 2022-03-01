## Outils pour travailler avec les DECP

#### Import des données JSON (.json)

- initialement `jsonlite::fromJSON()`
- si ***"Erreur : lexical error: invalid char in json text."*** --> `RJSONIO::fromJSON()`

#### Import des données JSON Lines (.jsonl)

- initialement `readLines("file.jsonl") %>% lapply(fromJSON)`
- .jsonl to .csv : `readLines("file.jsonl") %>% lapply(fromJSON) %>% lapply(unlist) %>% bind_rows()`

#### Comparer des JSON

- package [bergant/jsondiff](https://github.com/bergant/jsondiff), fonction `jsondiff::jsondiff(json1, json2)`
