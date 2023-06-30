---
title: 'DeepGO GO assignment evaluation in metagenome'
title_short: 'DeepGO metagenome evaluation'
tags:
  - GO
  - Microbiome
authors:
  - name: Rund E. Tawfiq
    orcid: 0000-0002-7052-573X
    affiliation: 1
  - name: Hiroshi Mori
    orcid: 0000-0003-0806-7704
    affiliation: 2
  - name: Robert Hoehndorf
    orcid: 0000-0001-8149-5890
    affiliation: 1
affiliations:
  - name: King Abdullah University of Science and Technology (KAUST) Thuwal, Kingdom of Saudi Arabia
    index: 1
  - name: National Institute of Genetics: Mishima, Japan
    index: 2
date: 30 June 2023
cito-bibliography: paper.bib
event: BH23JP
biohackathon_name: "BioHackathon Japan 2023"
biohackathon_url:   "https://2023.biohackathon.org/"
biohackathon_location: "Kagawa, Japan, 2023"
group: R2

# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/biohackathon-jp/bh23-deepgo-eval
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: Rund E. Tawfiq \emph{et al.}
---

# Background

Metagenomic sequencing data contains many genes from uncultured bacteria. Functional predictions of metagenomic genes are still challenging. Usually metagenomic gene function predictions are performed by protein sequence similarity searches against large reference protein sequence database like KEGG amino acid sequence database or InterPro. Protein sequence similarity searches using popular tools (e.g.,DIAMOND, MMSeqs2, InterProScan) with millions of query sequences needs many times and one of the largest bottle neck of microbiome research.
DeepGO and DeepGOPlus are deep learning based protein function prediction tools that assign Gene Ontology (GO) functions to protein sequences. DeepGOPlus combines a deep convolutional neural network (CNN) with sequence similarity-based predictions. The model combines motif-based function prediction and sequence similarity based search (if similar proteins with known functions are available). DeepGO incorporates protein structure information using ESMFold structure predictions as an additional feature, but is currently limited to predicting GO functions in the Molecular Function domain.
Both DeepGO and DeepGOPlus could overcome many limitations of large-scale protein function prediction in metagenomics. The models can perform predictions with high speed, can perform genome-scale annotations, and can be used to annotate newly sequenced organisms. In this project, we apply DeepGOPlus and newest DeepGO software for metagenome gene function prediction.

# Outcomes

Tool evaluation using metagenome data is usually difficult because we cannot know true community composition of the sequence data obtained. Mori group recently developed new human gut mock community that is constructed from 18 genome sequenced species. The Illumina NovaSeq 6000 250 bp paired-end metagenomic sequencing data of the DNA-mix of 18 species are assembled by MEGAHIT and predicted protein-coding genes by Prodigal metagenome option. Assembling result is good (N50 104.8 kb, 7118 contigs). These contigs encode 63537 protein sequences (average 302.6 AAs). We compared three GO assignment methods:
(i) InterProScan v5.62-94.0 and InterPro2GO
(ii) DeepGOPlus v1.0.1
(iii) DeepGO latest version (unpublished)
by counting how many GOs are shared between methods.

DeepGO/DeepGOPlus could assign GO functions more than 99% proteins (62920/63537 proteins in DeepGO). InterProScan could assign GO functions at 53.6% proteins (34078/63537 proteins).
The comparison result is summarized in the following Venn diagram.
The result indicates that DeepGO/DeepGOPlus assign many GOs. Mori checked some of the protein GO assignment result and noticed that DeepGO/DeepGOPlus tends to overassign broad range of related gene functions especially enzymes.

The calculation speed latest DeepGO is almost 10 times faster than InterProScan.

![Caption for BioHackrXiv logo figure](./biohackrxiv.png)

InterProScan	110 minutes	10 threads
DeepGO	27.5 minutes	3 threads
DeepGOPlus	48.4 minutes	16 threads

# Future work

The calculation speed of DeepGO is very good. But replacing the sequence similarity search in metagenomic analysis to DeepGO is still need careful quality assessment. DeepGO is currently intensely updating the tool algorithm. Since the upcoming DeepGO version will improve assignment results, the continuas evaluation of the gene functional prediction tools is necessary.

## Acknowledgements

We would like to thank the organizers for providing this Hackathon opportunity.

## References

1.hoge
2.fuga
3.haga
