### Machine learning of genotype-phenotype associations in colorectal cancer tumors from mutation

## Introduction
This project explores how genetic mutations relate to the tumor microenvironment (TME) in colorectal cancer. We focus on three types of mutations:
- **short tandem repeats (STRs)** – repeated sequences in dna.
- **single nucleotide polymorphisms (SNPs)** – single base-pair changes in the dna.
- **insertions and deletions (indels)** – small additions or removals of DNA bases.

By studying these mutation types, we aim to understand their connection to **mucin production** and **immune cell presence** in tumors.

Using machine learning, we need structured ways to represent mutations. Here is two approaches:
1. **Mutation counting**: for each sample, count the number of specific mutation types (number of SNPs, number of indels) and use these counts as features.

2. **Dimensionality reduction**: since mutation data is high-dimensional, apply methods like **principal component analysis (PCA)** to reduce feature numbers. This will be done separately for each mutation type before combining them in the ML model.

## Steps

1. **Literature overview**. Review existing studies on genetic mutations and their effect on the tumor microenvironment, focusing on mucin production and immune cell composition in colorectal cancer.

2. **Data preparation**. Extract mutation data from TCGA and preprocess it for machine learning. Determine the best way to represent different mutation types for predictive modeling.

3. **Machine learning**. Train models to predict mucin levels and immune cell presence based on mutation data. The goal is to find which mutation types are most important for understanding the tumor microenvironment.

   **3.1 Mutation representation**
   - use **mutation counting** and **dimensionality reduction** as described above.
   - normalize and preprocess features.

   **3.2 Model selection**
   - since the dataset has 300-500 samples, we will use models that work well with small datasets:
     - **random forest**
     - **support vector machines (SVM)** – useful for small datasets too
     - **gradient boosting**

   **3.3 Cross-validation and model evaluation**
   - use **k-fold cross-validation** (e.g., 5-fold) for reliable evaluation.
   - apply metrics like **roc-auc**, **accuracy**, and **f1-score** for classification, and **rmse** or **r²** for regression.
   - analyze feature importance to interpret model predictions.

4. **Interpretation**. Examine model results to find key genetic factors affecting mucin and immune cell levels. Compare predictions with existing research for validation.

## Potential analysis
Understanding **correlations between gene mutations and mucin expression** may help reveal how mutations influence mucin production.