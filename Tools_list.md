## Outils pour travailler avec les DECP

#### Import

##### Données JSON (.json)

- initialement `jsonlite::fromJSON()`
- si ***"Erreur : lexical error: invalid char in json text."*** --> `RJSONIO::fromJSON()`

#### Données JSON Lines (.jsonl)

- initialement `readLines("file.jsonl") %>% lapply(fromJSON)`


#### Aplatissement - dépend du format des données
  
- 1: `fromJSON(txt, flatten = T)`, 2: `as.data.frame(data$objet)`, 3: `uunest(data, cols = "nested_col", names_repair = "univeral")`
- 1: `purrr::map(
      .x = json,
      .y = data.frame(matrix(ncol = 1, nrow = 1)),
      .f = ~unnest(data.frame(    # on récupère chaque élément/variable qui nous intéresse, on les met dans un df
                     doi = .x$doi, 
                     year = .x$year,  
                     .x$author),
                 cols = "nested_col", names_repair = "universal"),   # on unnest une nested colonne
      .default = NA)`, 2: `extract_json_df %>% bind_rows()`
- 1: `fromJSON(txt)`, 2: `data.frame(Reduce(rbind, extraction))`

#### Comparer des JSON

- package [bergant/jsondiff](https://github.com/bergant/jsondiff), fonction `jsondiff::jsondiff(json1, json2)`
