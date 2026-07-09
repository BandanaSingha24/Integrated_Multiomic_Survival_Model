
# Integrated Multi-omic Survival Model

## **Project Overview**
This project focuses on integrating clinical, mRNA gene expression, and mutation data to build a robust survival risk stratification model.

## **Data Processing Steps and Results**

### **1. Clinical Data Processing**
* **Steps:** We cleaned the raw clinical data, handled missing values, and extracted essential features such as 'OS_months' and 'vital_status' for survival analysis.
* **Result:** Successfully generated a refined `processed_clinical_data.csv` file, ready for downstream modeling.

### **2. mRNA Gene Expression Data**
* **Steps:** The gene expression data was transposed and merged with the clinical data based on patient IDs. We also performed normalization and filtered out genes with low variation to improve data quality.
* **Result:** A high-quality, normalized gene expression matrix `processed_mrna_data.csv` was created.

### **3. Mutation Matrix**
* **Steps:** The raw mutation data was processed and converted into a binary matrix (0/1) to identify the presence or absence of gene mutations across patient samples.
* **Result:** Generated a clear `processed_mutation_matrix.csv` file, providing a detailed mutation profile for each patient.

## **Data Access**
The processed datasets can be downloaded from the release section of this repository:
* **[Insert your Release Link here]**
