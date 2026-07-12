
# Project: Multi-Omic Survival Analysis 
### Module 3_EDA

This module focuses on the Exploratory Data Analysis (EDA) of clinical and gene expression data to identify significant biomarkers.

### **Step 1: Data Integration (Merging Clinical & Gene Expression)**
* **Action**: Merged clinical data with gene expression data using `PATIENT_ID`.
* **Result**: Created a unified `merged_df` that aligns chemotherapy response with gene expression levels.

### **Step 2: Volcano Plot Analysis**
* **Action**: Generated a Volcano Plot to visualize differential gene expression.
* **Result**: Identified significantly up-regulated and down-regulated genes by plotting `log2 Fold Change` against `-log10(p-value)`.

### **Step 3: Correlation Heatmap**
* **Action**: Generated a heatmap to analyze correlations among the top 20 significant genes.
* **Result**: Visualized co-expression patterns, identifying clusters of genes that behave similarly across the dataset.

### **Step 4: Differential Expression Analysis (Box Plots)**
* **Action**: Compared gene expression levels between 'YES' and 'NO' chemotherapy groups using box plots.
* **Result**: Observed clear differential expression patterns, highlighting genes that are potentially impacted by chemotherapy.

### **Step 5: Statistical Summary & Feature Selection**
* **Action**: Shortlisted the top 10 most significant genes based on `p-value` and `log2FC`.
* **Result**: Exported a summary table as `significant_genes_summary.csv` to serve as a feature selection index for subsequent Supervised Learning and Survival Analysis modules.
