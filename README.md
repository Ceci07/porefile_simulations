# porefile analysis

## **Reference 16S rRNA gene sequences**
Reference sequences for the low complexity community (LCC) were retrived from the [ZymoBiomics Microbial Community Standard](https://files.zymoresearch.com/protocols/_d6300_zymobiomics_microbial_community_standard.pdf) web page.

The reference 16S rRNA gene sequences for the high complexity communities (HCC) were retrive from complete genomes from the [PATRIC database](https://www.bv-brc.org/view/Bacteria/2#view_tab=genomes). 16S rRNA genes were extracted using [barrnap](https://github.com/tseemann/barrnap) and used for ONT read simulation.

## **ONT read simulation**
ONT read simulation for the 16S rRNA gene references were performed with [Badread](https://github.com/rrwick/Badread) the "nanopore2020" error model and default identity (87.5% ± 5%, max. 97.5%)
Simulated reads were filtered with [Nanofilt](https://github.com/wdecoster/nanofilt) and only reads with a qscore above 10 and length between 1000 and 1700 bp were kept.

## **LCC and HCC generation**
Simulated reads were sampled using [fastq-tools](https://github.com/dcjones/fastq-tools) for each component. The LCC resambles mimics the relative abundance expected for the ZymoBiomics Microbial Community Standard. The HCC consisted in equal amounts of reads per components (human ~1% and environment ~8.3%).

## **Taxonomic classification**
Taxonomic classification of the LCC and HCC were performed with [porefile](https://github.com/microgenlab/porefile), [EMU](https://gitlab.com/treangenlab/emu) and [wf-metagenomics](https://github.com/epi2me-labs/wf-metagenomics) workflows.

## **Analysis**
[porefile](https://github.com/microgenlab/porefile) , [EMU](https://gitlab.com/treangenlab/emu) and [wf-metagenomics](https://github.com/epi2me-labs/wf-metagenomics) outputs were processed and compared in terms of percentage of correct and incorrect taxonomic classifications and the recovery of the expected relative abundance.
