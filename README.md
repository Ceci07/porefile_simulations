# Taxonomic classification of simulated communities

## **Reference 16S rRNA gene sequences**
Reference sequences for the low complexity community (LCC) were retrieved from the [ZymoBiomics Microbial Community Standard](https://files.zymoresearch.com/protocols/_d6300_zymobiomics_microbial_community_standard.pdf) web page.

The reference 16S rRNA gene sequences for the high complexity communities (HCC) were retrive from complete genomes from the [BACTERIAL AND VIRAL BIOINFORMATICS RESOURCE CENTER](https://www.bv-brc.org/view/Bacteria/2#view_tab=genomes). 16S rRNA genes sequences were extracted using [barrnap](https://github.com/tseemann/barrnap) and used for ONT read simulation.

## **ONT read simulation**
ONT read simulation for the 16S rRNA gene references were performed with [Badread](https://github.com/rrwick/Badread) using the "nanopore2020" error model with a read length distribution of 1500 ± 200 bp and default identity (87.5% ± 5%, max. 97.5%).
Simulated reads were then filtered with [Nanofilt](https://github.com/wdecoster/nanofilt) and only reads with a quality score above 10 and length between 1000 and 1700 bp were kept for analysis.

## **LCC and HCC generation**
Simulated reads were sampled using [fastq-tools](https://github.com/dcjones/fastq-tools) for each component. The LCC reads were combined to mimic the relative abundance expected for the ZymoBiomics Microbial Community Standard components. Ten replicates were generatd from the simulated sampled reads. 
The HCC consisted of equal amounts of reads per component. The expected relative abundance for each component was ~1% for the human simulated dataset (n = 101) and ~8.3% for the environment simulated dataset (n = 12).

## **Taxonomic classification**
Taxonomic classification of the LCC and HCC were performed with [porefile](https://github.com/microgenlab/porefile), [EMU](https://gitlab.com/treangenlab/emu) and [wf-metagenomics](https://github.com/epi2me-labs/wf-metagenomics) workflows.

## **Analysis**
[porefile](https://github.com/microgenlab/porefile), [EMU](https://gitlab.com/treangenlab/emu) and [wf-metagenomics](https://github.com/epi2me-labs/wf-metagenomics) outputs were processed and compared in terms of percentage of correct and incorrect taxonomic classifications and the recovery of the expected relative abundance (based on linear fit between expected and observed relative abundannces and the root mean square error or RMSE). False negatives (FN) were defined as the number of reads that were not classified at species level, true positives (TP) were defined as the number of reads classified at species level of the known LCC components and false positives (FP) were defined as the species level classifications that do not correspond to the LCC components.
