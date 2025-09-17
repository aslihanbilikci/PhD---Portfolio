# 🧬 MI vs Sham RNA-seq Analysis

## Overview
This repository contains the full analysis pipeline for RNA-seq data comparing **myocardial infarction (MI)** and **sham control** samples in mouse. The project integrates raw quantification, quality control, normalization, **differential expression analysis (DEA)**, and **functional enrichment** (KEGG/GSEA).  

The workflow is implemented in R (`MI_ShAM_RNAseq.Rmd`) and designed for reproducibility and transparency in systems biology research.  

---

## Objectives
- Import and preprocess transcript quantifications.  
- Perform gene-level count aggregation.  
- Conduct **differential expression analysis (DEA)** with DESeq2.  
- Run **functional enrichment** using KEGG pathways (fgsea).  
- Generate publication-ready figures and tables.  

---

## Workflow  

1. **Data Import & Preprocessing**  
   - Transcript quantification via *Kallisto*  
   - Aggregation to gene counts with **tximport**  
   - Metadata parsing (treatment, time, replicate)  

2. **Quality Control**  
   - Count distribution and PCA  
   - Outlier detection  

3. **Differential Expression**  
   - DEA using **DESeq2**  
   - Volcano plots, MA plots  
   - Results exported as `.csv`  

4. **Functional Enrichment**  
   - Gene set enrichment analysis with **fgsea**  
   - KEGG pathways mapped via `org.Mm.eg.db`  
   - Ranked statistics (log2FC, Wald test)  

---

## Repository Structure  

```
├── MI_ShAM_RNAseq.Rmd    # Main analysis pipeline (R Markdown)
├── results/              # DEA results, enrichment outputs
├── figures/              # QC plots, PCA, volcano plots, KEGG results
└── data/                 # Input quantifications, metadata (not included in repo)
```

---

## Dependencies  

- **R (≥4.3)**  
- Key packages:  
  - [tximport](https://bioconductor.org/packages/release/bioc/html/tximport.html)  
  - [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)  
  - [fgsea](https://bioconductor.org/packages/release/bioc/html/fgsea.html)  
  - [org.Mm.eg.db](https://bioconductor.org/packages/release/data/annotation/html/org.Mm.eg.db.html)  
  - dplyr, ggplot2, AnnotationDbi  

Install missing dependencies in R:  

```r
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install(c("tximport", "DESeq2", "fgsea", "org.Mm.eg.db"))
install.packages(c("dplyr", "ggplot2"))
```

---

## Usage  

1. Clone the repository:  

```bash
git clone https://github.com/yourusername/MI-vs-Sham-RNAseq.git
cd MI-vs-Sham-RNAseq
```

2. Open `MI_ShAM_RNAseq.Rmd` in RStudio.  
3. Knit to generate the full report (HTML/PDF).  
4. Results will be saved in `/results/` and plots in `/figures/`.  

---

## Results  

- **Differentially expressed genes (DEGs)** between MI and sham conditions.  
- **Pathway enrichment** highlighting perturbed metabolic and signaling pathways.  
- Exported CSV files for reproducibility and downstream integration.  

---

## Citation  

If you use this pipeline in your research, please cite:  

> Bılıkçı, A. (2025). *MI vs Sham RNA-seq Analysis Pipeline*. GitHub repository.  

---

## License  

This project is released under the **MIT License**.  
