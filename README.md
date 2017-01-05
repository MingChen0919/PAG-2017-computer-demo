# PAG 2017 computer demo

## Tripal Elasticsearch

### Site wide search (Advanced search)

* **Fuzzy search**: When you don't know how to exactly spell your keywords, you use `fuzzy` search. `fuzzy` search allows you to search for similar words. You use the `~` at the end of your keyword for `fuzzy` search (`keyword~`). Examples:

  + `sequeeence~` -> `sequence`
  + `alnus  rhmobifla~` -> `Alnus rhombifolia`

* **Wildcard search** with `*`. Examples:

  + `genom* sequence` -> `genome`, `genomic`, `genomics` ...
  + `Lir*dron tulipifera` -> `Liriodendron tulipifera`

* **Regular expression search**: wrapping keywords with forward slash (`/`). Examples:

  + `/transcriptom[a-z]+/` -> `transcriptome`, `transcriptomes`, `transcriptomics` ...

* **Boolean operators**: `+` and `-`. `+` means must present; `-` means must not present. Examples:

  + `+"green ash" +transcriptome -genome`
  + `+"green ash" -transcriptome +genome`
