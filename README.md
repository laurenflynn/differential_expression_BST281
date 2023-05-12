# Differential Expression BST281

### Lauren Flynn

Differential expression analysis using mRNA data for head and neck squamous cell carcinoma

For final project in BST 281 Spring 2023

Exploring differential expression using DESeq2 and edgeR.


#### Input

**Original data source**: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE226134 using pre-treatment samples from GSE226134_CK_10__norm.xlsx

**data/input/Integer_mRNA_counts.csv**: This file has the pre-treatment sample expression values. QC was conducted by Lauren Mock. It contains 59 samples and 9223 genes with expression values. The count data was transformed from normalized to integer read counts. Each row is a gene and each column is a sample.

**data/input/Patient_properties.csv**: This file includes the segment display name (the sample ID) and the metastatic status of each sample. Each row is a sample.

#### Code

**differential_expression.qmd**: A Quarto document with the code for all of the differential expression analysis, written in R. Included are DESeq analysis and edgeR tests to check for genes with differential expression between the metastatic and non-metastatic groups, respectively.


#### Output

**data/output/DESeq_Normalized.txt**: A text file with the gene counts from the input mRNA counts file normalized using DESeq for use in GSEA. 



**data/output/deseq_diff_exp_results.csv**: A CSV file that contains the differentially expressed genes from DESeq. There are 113 genes included. They had a log2 fold change greater than 1 and an adjusted p-value less than 0.05 using the Benjamini Hochberg correction. 

**data/output/deseq_edger_overlap_diff_exp_results.csv**: A CSV file that contains the differentially expressed genes from DESeq and EdgeR. There are 106 genes included. They had a log2 fold change greater than 1 and an adjusted p-value less than 0.05 using the Benjamini Hochberg correction. This is a subset of deseq_diff_exp_results.csv. 

##### Data Dictionary for deseq_diff_exp_results.csv and deseq_edger_overlap_diff_exp_results.csv:


| Variable      | Description |
| ----------- | ----------- |
| gene      | Name of the gene identified       |
| baseMean   | mean of normalized counts for all samples (from DESeq results)        |
| log2FoldChange | log2 fold change (MLE): condition metastasis vs non-metastasis; non-metastasis is the reference group (from DESeq results)|
| lfcSE | standard error for log2 fold change (from DESeq results) |
| stat | Wald statistic: metastatic vs non-metastatic (from DESeq results)|
| pvalue | Wald statistic p-value (from DESeq results)|
| padj | Benjamini-Hochberg adjusted p-values (from DESeq results)|


