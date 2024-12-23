# Gene-Expression-Analysis

This Quarto file contains each step involved in carrying out a gene expression analysis for HER2/ERBB2+ breast cancer.

1. Untar the folder and extract the files: in this section, we extracted the compressed dataset files.

2. Read the RNA-seq files: here, we read the three files used in our analysis, `data_mrna_seq_v2_resem.txt`, `data_clinical_patient.txt` and `data_cna.txt`

3. Match the RNA-seq patient ids with the CNA ids and the Patient Data ids: here, we matched patient identifiers across our three datasets. In order to carry out this matching, we first had to standardise patient IDs. Then, we compared IDs across the three datasets, ensuring that each one was present in each dataset. IDs that were present in all three datasets were kept.
   
4. Create metadata using the CNA level of ERBB2+ (greater than 0 means amplified): in this section, we identified samples with ERBB2 amplification and created metadata for further analysis.
   
5. Normalize data using DESeq2: next, we normalised RNA-seq counts using DESeq2 to make them comparable across samples.

6. Obtain differentially expressed genes: here, we identified the top 10 differentially expressed genes, ranking them by adjusted p-value.

7. Perform a Pathway Enrichment Analysis: we then carried out a Gene Ontology enrichment analysis to identify biological pathways associated with differentially expressed genes.

8. Get the variance stabilised transformed expression values: in this section, we prepared the RNA-seq data for further analysis by stabilising variance across samples. The variance-stabilisating transformation (VST) is applied here to reduce the effects of large differences in variances.

9. With the vst values obtain a PCA plot and a heatmap: after getting the variance stabilised transformed expression values we carried out a Principal Component Analysis (PCA) plot and a heatmap of the top differentially expressed genes.

10. With the vst values of the DE genes generate an overall survival model using the glmnet package: here, we build a survival model using Lasso-regularised Cox regression model to predict patient survival times based on gene expression data.

The following R packages were to run this analysis:
* `DESeq2` was used for normalisation and differential expression analysis
* `clusterProfiler`, `org.Hs.eg.db`, `enrichplot` and `ggplot2` was used for pathway enrichment analysis
* `glmnet` and `survival` was used for creating a survival model
* `pheatmap` and `ggplot2` was used to create our heatmap
