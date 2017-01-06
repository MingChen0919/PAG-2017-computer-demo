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

* **`AND`, `OR`, `NOT` operator and combination search**. Examples:

  + `"heat stress" AND ("Castanea mollissima" OR "green ash") NOT "heat shock"`




## Tripal Expression Analysis

### Expression comparison between `heat shock` vs `NOT "heat shock"` genes from green ash.

**Heat shock induced gene expression can help limit the damage caused by stress**(Arya, et al., 2007).

* `heat shock` genes

```
Fraxinus_pennsylvanica_120313_comp18083_c0_seq1,
Fraxinus_pennsylvanica_120313_comp15550_c0_seq1,
Fraxinus_pennsylvanica_120313_comp13944_c0_seq1,
Fraxinus_pennsylvanica_120313_comp64929_c0_seq2,
Fraxinus_pennsylvanica_120313_comp52334_c0_seq1,
Fraxinus_pennsylvanica_120313_comp56548_c0_seq1,
Fraxinus_pennsylvanica_120313_comp56481_c0_seq1,
Fraxinus_pennsylvanica_120313_comp56481_c0_seq2
```

* `not heat shock` genes

```
Fraxinus_pennsylvanica_120313_comp138340_c0_seq1,
Fraxinus_pennsylvanica_120313_comp13845_c0_seq1,
Fraxinus_pennsylvanica_120313_comp13841_c0_seq1,
Fraxinus_pennsylvanica_120313_comp13845_c0_seq2,
Fraxinus_pennsylvanica_120313_comp1384_c0_seq1,
Fraxinus_pennsylvanica_120313_comp138541_c0_seq1,
Fraxinus_pennsylvanica_120313_comp138804_c0_seq1,
Fraxinus_pennsylvanica_120313_comp138820_c0_seq1
```
