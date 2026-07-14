
# Project: Multi-Omic Survival Analysis 
### Module 3_EDA

### --------------Clinical_Gene_expression_marged_EDA ------------------------
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

### -----------------MUTATION ANALYSIS: COMPLETE PIPELINE SUMMARY ------------------------------

### PART 1: MUTATION EDA & EXPLORATORY DATA ANALYSIS
* **Step 1 (Data Prep)**: Loaded 'data_mutations.txt' and performed essential data cleaning.
* **Step 2 (Top Mutated Genes)**: Identified top 10 genes; PIK3CA confirmed as the primary driver (Hero Gene).## Step 3 (TMB Calculation): ## ##  * **step 3 (TMB Calculation)**: Calculated Tumor Mutational Burden (TMB) to assess genomic instability.
* **Step 4 (Onco-Plot & Visualization)**: Generated Onco-Plots to visualize mutation frequency and types.*# **tep 5 (Sample Statistics)**:                    Performed sample-level analysis to understand mutation burden variations.
* **Result**s: Established a comprehensive landscape of the cancer genomic profile.

### PART 2: ADVANCED PROFILING & FEATURE ENGINEERING
* **Step 1 (Categorical Impact Quantification)**: Conducted quantitative analysis of mutation impacts.
* **Step 2 (Epistatic Pair Feature Engineering)**: Created correlation heatmaps to identify co-occurrence patterns between genes.
* **Step 3 (Hotspot Analysis)**: Pinpointed critical PIK3CA hotspots, specifically p.H1047R and p.E545K.
* **Step 4 (Functional & Structural Mapping)**: Analyzed biological impacts of variants and their structural implications.
* **Step 5 (Data Export)**: Exported processed datasets (epistatic_pairs.csv, functional_mutation_impact.csv) for future use.
* **Results**: Established a robust structural/functional mutation profile, providing a foundation for Module 7 integration.  
