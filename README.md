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

### 1.Upregulation Sigma54

Calculated Log2FC from evolved vs ancestral strains. Annotates with sigma54 EBPs and targets. Data visualization and σ⁵⁴-target gene vs other genes wilcoxon (Figure 1a, Figure 3b).

### 2.Upregulation Across Events

UpSet and Spearman Correlation Plots (Figure 1b, Figure 2b). Fisher’s Exact Tests. 

### 4.Rewiring Speed

Rha vs No Rha barplot (Figure 2a). Withn strain σ⁵⁴-target expression as a function of rhamnose induction Wilcoxon. 

### 6.Mutation to Regulatory Prediction

FGSEA and STRING expanded FGSEA (Figure 3a).

### 7.Variant Calling

Alignment and variant calling. Input WGS reads available on SRA at BioProject ID: PRJNA992893.

### 8.Variant Calling Analysis
Cluster mutations and create binary heatmap (Figure 4).

```
