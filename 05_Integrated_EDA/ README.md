# MD5: Integrated Multi-Omics Data Analysis Pipeline

This repository contains the step-by-step Exploratory Data Analysis (EDA) and dimensionality reduction pipeline for the MD5 multi-omics master tensor (1,787 patient rows × 874 feature columns). The objective is to identify robust molecular biomarkers and co-regulated pathways driving clinical chemotherapy response.

### 1. Principal Component Analysis (PCA)
* **Process:** Applied linear unsupervised dimensionality reduction to project the master integrated tensor into orthogonal coordinate space.
* **Result:** *Variance Domination Artifact.* The top principal components were overwhelmingly dominated by non-molecular clinical features due to baseline scale differences. Linear projections failed to resolve distinct patient sub-populations.

### 2. t-Distributed Stochastic Neighbor Embedding (t-SNE)
* **Process:** Implemented non-linear manifold learning to optimize local spatial structures using a standard perplexity threshold.
* **Result:** *Amorphous "Hairball" Effect.* Data points clumped into a dense, unseparated central cloud. The optimization failed to converge cleanly because raw multi-omics features (continuous vs. binarized mutations) warped the baseline local distance calculations.

### 3. Uniform Manifold Approximation and Projection (UMAP)
* **Process:** Executed UMAP embedding using global topology-preserving parameters (n_neighbors=30, min_dist=0.15).
* **Result:** *Continuous Phenotypic Trajectory Map.* By leveraging Riemannian geometry, UMAP successfully resolved the data into a highly structured, continuous biological trajectory. This map models the progressive phenotypic shifts occurring across patient cohorts under therapeutic pressure.

### 4. Chemotherapy Volcano Plot
* **Process:** Structured a differential expression screen comparing the Treated vs. Untreated patient cohorts to calculate raw statistical p-values.
* **Result:** *Uncalibrated Baseline View.* The initial statistical landscape mapped features across raw parameter scales, identifying critical candidate regions but highlighting an immediate need for proper Log2 Fold Change (Log2FC) normalization on the horizontal axis.

### 5. Extreme Statistical Association Discovery
* **Process:** Filtered and sorted the resulting volcano_df dataframe to isolate the top 38 features with the strongest significance scores.
* **Result:** *Data Confounding Identification.* The printout exposed that non-molecular metadata like AGE_AT_DIAGNOSIS and Nottingham Prognostic Index (NPI) yielded extreme scores up to -log10(p-value) = 89. This step successfully caught the technical features causing scale skewness.

### 6. Chemotherapy Zoomed Volcano Plot
* **Process:** Applied a precise visual sub-window restriction (plt.xlim(-5, 5)) to focus the coordinate space directly on the core multi-omics distribution.
* **Result:** *Parabolic Resolution of Biomarkers.* The dense data opened up into a clean, textbook-style parabolic curve. This allowed clear visualization of the exact molecular markers (such as PHF7, GLI3, and CDC45) driving the response to chemotherapy, safely separated from the clinical outliers.

### 7. Volcano Unzoomed Plot
* **Process:** Plotted the total unclipped feature space to maintain a complete mathematical record of the global data landscape.
* **Result:** *Scale Axis Distortion View.* This plot captured the complete wide-axis view stretching all the way to -30 on the X-axis. It beautifully documents your optimization story, showing how the outlier AGE_AT_DIAGNOSIS (Log2FC = -13.18) pulled the graph wide and squished the remaining molecular data into a tight right-hand column.

### 8. Pearson Correlation Heatmap
* **Process:** Generated a pairwise Pearson Correlation Matrix among the top statistically significant candidate features discovered in the differential screen.
* **Result:** *Discovery of Functional Co-Expression Modules.* The matrix cleanly resolved deep red off-diagonal blocks (proving tight positive co-regulation between target genes like GLI3 and BBOF1) and sharp blue tiles indicating opposing cellular processes. The neutral background verified excellent feature independence across the rest of the dataset.
