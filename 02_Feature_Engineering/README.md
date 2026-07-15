# Module 2: Multi-Omics Feature Engineering & Scalability Alignments

This module transforms processed multi-omics data into machine-learning-ready tensors by executing categorical encodings, high-dimensional variance scaling, and domain-specific biomarker extraction.

## 1. Clinical Feature Engineering
* **Categorical Standardization:** Corrected text incongruencies (e.g., standardizing mixed formats like "Pos" and "Positive") within critical hormone receptor annotations.
* **Encoding Strategies:** 
  * Applied binary map encoding (0/1) to dual-state clinical tracks (CHEMOTHERAPY, HORMONE_THERAPY).
  * Deployed One-Hot Encoding (pd.get_dummies with reference drop) to multi-class variables (CELLULARITY, HER2_STATUS, ONCOTREE_CODE, SAMPLE_TYPE) to eliminate artificial weight rankings during backpropagation.
* **Z-Score Scaling:** Normalized divergent continuous ranges (LYMPH_NODES_EXAMINED_POSITIVE, NPI, TUMOR_SIZE) using StandardScaler to bring feature variances to 1 and means to 0.
* **[RESULTS]:** 
  * Core clinical frame fully converted. Datatype audit confirmed that *only ['PATIENT_ID'] remains as a non-numeric string column*, making the dataframe 100% compliant for multi-omics array concatenation.

## 2. Somatic Mutation Feature Engineering
* **Biomarker Synthesis (TMB Proxy):** Retained individual binarized gene flags for deep interaction learning while engineering a high-utility *Tumor Mutational Burden (TMB)* proxy metric by aggregating raw mutation counts per patient profile. This bridges computer science scalability with translational oncology.
* **[RESULTS]:** 
  * New engineered feature added. Final Mutation matrix shape expanded from 174 columns to *(2358, 175)* to safely accommodate the TUMOR_MUTATIONAL_BURDEN continuous scoring metric.

## 3. Transcriptomics Feature Engineering
* **Biological Noise Elimination:** Screened the expression header space to detect and drop non-protein coding RNA loci and uncharacterized genomic regions (specifically *LOC* prefix genes) that lack functional annotation, significantly improving the signal-to-noise ratio.
* **Continuous Variance Scaling:** Centred and scaled the remaining highly dynamic gene signatures using Z-score transformations, ensuring high-baseline expressions do not disproportionately dominate downstream multi-omics model weights.
* **[RESULTS]:** 
  * Filtering algorithm dropped 4 non-protein-coding unannotated features.
  * Final finalized Transcriptomics shape locked at *(1980, 538)*, yielding 537 clean, z-score standardized, protein-coding gene expression features ready for integration.
 
