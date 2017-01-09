# PAG 2017 computer demo

* [HGD Database Navigation](#hgd-database-navigation)
* [Tripal Elasticsearch](#tripal-elasticsearch)
* [Tripal Expression Analysis](#tripal-expression-analysis)

## HGD Database Navigation
### Genetic resources

* transcriptomes from 15 species (click **Genomic Data**->**Transcriptomes**->**Fraxinus pennsylvanica 120313**)
    + transcriptome analysis information
    + assembly reports
    + annotation data downloadable
    + raw reads links to NCBI SRA

* SSRs (click **Genomic Data**->**gSSRs**)
    + predicted transcriptomic SSRs (15 species)
    + predicted genomic SSRs (10 species)
    + confirmed SSRs markers (8 species)
* Reference genome
    + Chinese Chestnut Genome and QTL Sequences v1.0 (click **Genomic Data**->**Chestnut Genome**)
    + Chestnut Physical Map (click **Genomic Data**->**Chestnut Physical Map**)
    
* Organism page (Click **Trees**->**Fraxinus pennsylvanica**: [http://www.hardwoodgenomics.org/organism/Fraxinus/pennsylvanica](http://www.hardwoodgenomics.org/organism/Fraxinus/pennsylvanica))
    + Brief introduction to a species
    + Links to all genetic resources that are associated with this species.

### Tools

* Cmap (**Tools**->**Cmap**)
* JBrowse/Webapollo (**Tools**->**JBrowse/WebApollo - Chestnut Genome Sequence**)
* SyMap (**Tools**->**Chinese Chestnut SyMAP**)
* Blast
* Expression Visualization

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
* Search interfaces and results are displayed with separated drupal blocks.



## Tripal Expression Analysis


### Data collection
* Example: [http://www.hardwoodgenomics.org/feature/Fraxinus_pennsylvanica_120313_comp61194_c0_seq5](http://www.hardwoodgenomics.org/feature/Fraxinus_pennsylvanica_120313_comp61194_c0_seq5)

  + **Expression data analysis information**: click **Analyses**->**Green Ash Ozone Treatments** to go to the analysis content page
  + **Biomaterials information**: click **Expression**->**Any bar of the figure** to go to the biomaterial content page
  + **Expression values**: see the figure(sort, tile/chart).

### Genes Expression Visualization

  * Go to the **Expression Visualization** interface
  * Provide a list of genes separated by comma(`,`)
  * Click `Display Expression Heatmap` button to generate the heatmap.
  * Some example genes:
  
```
Fraxinus_pennsylvanica_120313_comp18083_c0_seq1,
Fraxinus_pennsylvanica_120313_comp15550_c0_seq1,
Fraxinus_pennsylvanica_120313_comp13944_c0_seq1,
Fraxinus_pennsylvanica_120313_comp64929_c0_seq2,
Fraxinus_pennsylvanica_120313_comp52334_c0_seq1,
Fraxinus_pennsylvanica_120313_comp56548_c0_seq1,
Fraxinus_pennsylvanica_120313_comp56481_c0_seq1,
Fraxinus_pennsylvanica_120313_comp56481_c0_seq2,
Fraxinus_pennsylvanica_120313_comp56481_c0_seq3,
Fraxinus_pennsylvanica_120313_comp56092_c0_seq1
```


### A use case: expression comparison between `heat shock` vs `kinase` genes from green ash.

**Heat shock induced gene expression can help limit the damage caused by stress**(Arya, et al., 2007).

* Go to **transcripts search** interface (click **Transcripts search**)
    + Search `"heat shock"` for **Hit Description** and select `Fraxinus pennsylvanica` for **Abbreviation**, and download the search results.
    +  Search `kinase NOT heat` for **Hit Description** and select `Fraxinus pennsylvanica` for **Abbreviation**, and download the search results.

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

* Go to **Expression Visualization** interface to generate the heatmap.
