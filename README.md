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


### Database table specific search

The Tripal Elasticsearch module allows you to index single tables and build search interface for them. All the advanced search methods that are available to the site wide search can be applied to table specific search. 

Implementation examples in the HGD

* **transcripts search** (A couple of examples):

  1. search keywords: 
    + Abbreviation: `Fraxinus pennsylvanica`
    + Unique name: ` `
    + Hit Description: `"heat shock"`
    
  2. search keywords: 
    + Abbreviation: `Fraxinus pennsylvanica`
    + Unique name: ` `
    + Hit Description: `"heat shock" NOT "Arabidopsis thaliana"`

* **Organisms**
* Search with no keywords input will return all available records
* Search results downloadable as csv file.



## Tripal Expression Analysis

### Expression comparison between `heat shock` vs `NOT "heat shock"` genes from green ash.

**Heat shock induced gene expression can help limit the damage caused by stress**(Arya, et al., 2007).

* Search keywords: `"heat shock"` genes([heat-shock-genes.txt](heat-shock-genes.txt))

```
Fraxinus_pennsylvanica_120313_comp59663_c0_seq1,
Fraxinus_pennsylvanica_120313_comp59663_c0_seq2,
Fraxinus_pennsylvanica_120313_comp56723_c0_seq1,
Fraxinus_pennsylvanica_120313_comp60325_c0_seq16,
Fraxinus_pennsylvanica_120313_comp61194_c0_seq4,
Fraxinus_pennsylvanica_120313_comp61194_c0_seq5,
Fraxinus_pennsylvanica_120313_comp61194_c0_seq8,
Fraxinus_pennsylvanica_120313_comp61194_c0_seq6,
```

* Search keywords: `+kinase -heat` genes([kinase-not-heat-genes.txt](kinase-not-heat-genes.txt))

```
Fraxinus_pennsylvanica_120313_comp59251_c0_seq8,
Fraxinus_pennsylvanica_120313_comp31358_c0_seq1,
Fraxinus_pennsylvanica_120313_comp63273_c0_seq25,
Fraxinus_pennsylvanica_120313_comp63273_c0_seq3,
Fraxinus_pennsylvanica_120313_comp48376_c0_seq1,
Fraxinus_pennsylvanica_120313_comp48376_c0_seq2,
Fraxinus_pennsylvanica_120313_comp40803_c0_seq1,
Fraxinus_pennsylvanica_120313_comp31272_c0_seq1
```
