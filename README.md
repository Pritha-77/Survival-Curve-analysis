# 🧬 TCGA-COAD Survival Analysis using PRKCZ Expression

This repository contains an R script for conducting survival analysis on **TCGA-COAD (colon adenocarcinoma)** patients based on the expression of the **PRKCZ** gene. The analysis uses publicly available clinical and RNA-Seq data from the [GDC Data Portal](https://portal.gdc.cancer.gov/), accessed via the `TCGAbiolinks` package.

## 📦 Requirements

📈 Statistical Test

survdiff(Surv(overall_survival, deceased) ~ strata, data = coad_PRKCZ)
This performs a log-rank test comparing the survival distributions between the high- and low-expression groups.
🧪 Customization
You can easily modify the script to perform survival analysis for any gene:
filter(gene_name == "YOUR_GENE")
Just replace "PRKCZ" with your gene of interest.


Make sure you have the following R packages installed:

```R
install.packages("survminer")
install.packages("survival")
install.packages("tidyverse")
BiocManager::install(c("TCGAbiolinks", "SummarizedExperiment", "DESeq2"))
🛠 Steps Performed
1.	Download clinical data for the TCGA-COAD cohort using TCGAbiolinks.
2.	Preprocess clinical variables like vital_status, days_to_death, and days_to_last_follow_up.
3.	Download RNA-Seq expression data (STAR-counts workflow) from TCGA.
4.	Preprocess and normalize expression data using DESeq2::vst.
5.	Subset the gene of interest (PRKCZ) and label samples as HIGH or LOW based on the median expression.
6.	Merge clinical and expression data by TCGA barcodes.
7.	Fit Kaplan-Meier survival curves and perform a log-rank test to assess significance.




