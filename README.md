# Transcriptional Consequences of σ⁵⁴ Regulatory Rewiring in *Pseudomonas fluorescens*

## Overview

This repository contains all R code and analysis notebooks for the study of transcriptional 
rewiring in *Pseudomonas fluorescens*. When the master flagellar regulator FleQ is deleted, 
bacteria recover motility by co-opting σ⁵⁴ enhancer binding proteins (EBPs) into a new regulatory role.

We used RNA-sequencing data from four independently evolved strains (0286, 2209, 2630, 4895), 
each carrying a different σ⁵⁴ EBP under rhamnose-inducible control, to characterize the 
downstream transcriptional consequences of rewiring. Whole genome sequencing was used to 
identify candidate mutations driving convergent rewiring phenotypes.

**Key findings:**
- σ⁵⁴-target genes show consistent upregulation across all four strains under rhamnose induction, supporting a shared pattern of transcription factor-driven activation
- Strains diverge under basal conditions: 0286 and 2630 show **inducible rewiring** (σ⁵⁴ activation depends on rhamnose), while 2209 and 4895 show **constitutive rewiring** (σ⁵⁴ targets activated even without rhamnose)
- Convergent constitutive rewiring in 2209 and 4895 is associated with shared frameshift indels in *algB* (PFLU_RS00440) and mutations in the PFLU1131/1132 pathway, implicating loss-of-function disruption of a competing σ⁵⁴ EBP
- NorR (PFLU_5143) is strongly downregulated in both constitutive rewiring strains, suggesting a shared upstream regulatory shift

---

## Repository Structure

```

1.Upregulation Sigma54

Calculated Log2FC from evolved vs ancestral strains. Annotates with sigma54 EBPs and targets. Data visualization and σ⁵⁴-target gene vs other genes wilcoxon (Figure 1a, Figure 3b).

2.Upregulation Across Events

UpSet and Spearman Correlation Plots (Figure 1b, Figure 2b). Fisher’s Exact Tests. 

4.Rewiring Speed

Rha vs No Rha barplot (Figure 2a). Withn strain σ⁵⁴-target expression as a function of rhamnose induction Wilcoxon. 

6.Mutation to Regulatory Prediction

FGSEA and STRING expanded FGSEA (Figure 3a).

7.Variant Calling

Alignment and variant calling. Input WGS reads available on SRA at BioProject ID: PRJNA992893.

8.Variant Calling Analysis
Cluster mutations and create binary heatmap (Figure 4).

figures/
output figures

input_data/
Processed input files (counts, annotations)

results/
Analysis outputs
```

## Data Availability

RNA-sequencing and whole genome sequencing data are available on NCBI SRA:  
**BioProject: [PRJNA992893](https://www.ncbi.nlm.nih.gov/bioproject/PRJNA992893)**

σ⁵⁴ target gene annotations used in this study are from [Shepherd et al., 2023 (*PLoS Biology*)](https://doi.org/10.1371/journal.pbio.3002348).  
σ⁵⁴ promoter predictions were generated using [ProPr54](https://doi.org/10.1093/nargab/lqae188).

## Methods Summary

**RNA-seq analysis** — DESeq2 size-factor normalization; log₂ fold change calculated between evolved and ancestral isolates per strain × condition. Wilcoxon rank-sum tests used to compare σ⁵⁴-target vs. non-target gene distributions. Pairwise Spearman correlations and UpSet plots used to characterize cross-strain transcriptional convergence.

**Gene set enrichment** — FGSEA with STRING-expanded pathway gene sets (anti-sigma system, glycine cleavage, pyrimidine-aspartate metabolism, nitric oxide reductase, σ⁵⁴ targets). Enrichment defined at Benjamini-Hochberg adjusted p ≤ 0.05.

**Variant calling** — Paired-end WGS reads aligned to *P. fluorescens* SBW25 reference with minimap2; variants called with bcftools mpileup/call; mutations clustered in 500 bp windows and compared across strains as binary presence-absence matrices. Candidate variants visualized in IGV.

All analyses conducted in R. See individual `.Rmd` notebooks for full reproducible code.

## Dependencies

**R packages:** `DESeq2`, `fgsea`, `ggplot2`, `tidyverse`, `UpSetR`, `ComplexHeatmap`  
**External tools:** `minimap2`, `samtools`, `bcftools`

## Author

Griffin Kramer — [linkedin.com/in/griffin-d-kramer](https://www.linkedin.com/in/griffin-d-kramer)  

