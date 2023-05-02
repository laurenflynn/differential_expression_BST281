# Differential Expression BST281

### Lauren Flynn

Differential expression analysis using mRNA data for head and neck squamous cell carcinoma

For final project in BST 281 Spring 2023

Exploring results between limma-voom, t-tests, and Wilcoxon rank sum tests.

Original data source: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE226134 using pre-treatment samples from GSE226134_CK_10__norm.xlsx

data/input/JoinedWide.csv: This file has the pre-treatment sample expression values and combines the sample properties with the read counts. QC was conducted by Lauren Mock. It contains 59 samples and 9223 genes with expression values. It also includes information about the samples, with the 'METASTATIC' variable of interest here. Each row is a sample and each column describes either a sample property or a normalized gene read count for that sample. 

differential_expression.qmd: A Quarto document with the code for all of the differential expression analysis, written in R. Included are DESeq analysis, t-tests, and Wilcoxon rank sum tests to check for genes with differential expression between the metastatic and non-metastatic groups, respectively.

data/output/metastasis_results.csv: A CSV file that contains the differentially expressed genes from DESeq and EdgeR. There are 106 genes included. They had a log2 fold change greater than 1 and an adjusted p-value less than 0.05 using the Benjamini Hochberg correction. 

Data Dictionary for metastasis_results.csv:


| Variable      | Description |
| ----------- | ----------- |
| gene      | Name of the gene identified       |
| baseMean   | mean of normalized counts for all samples (from DESeq results)        |
| log2FoldChange | log2 fold change (MLE): condition metastasis vs non-metastasis; non-metastasis is the reference group (from DESeq results)|
| lfcSE | standard error for log2 fold change (from DESeq results) |
| stat | Wald statistic: metastatic vs non-metastatic (from DESeq results)|
| pvalue | Wald statistic p-value (from DESeq results)|
| padj | Benjamini-Hochberg adjusted p-values (from DESeq results)|


