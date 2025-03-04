### Machine learning of genotype-phenotype associations in colorectal cancer tumors from mutation

## Introduction
This project aims to uncover relationships between genetic mutations and tumor microenvironment (TME) characteristics in colorectal cancer. We focus on three types of mutations:
- **STRs (Short Tandem Repeats)** – repeated sequences in DNA.
- **SNPs (Single Nucleotide Polymorphisms)** – single base-pair changes in the DNA.
- **Indels (Insertions and Deletions)** – small insertions or deletions of bases in the DNA.

By analyzing these mutation types, we will explore their association with **mucin production** and **immune cells** in tumors. 

## Steps

1. **Literature overview**. Review existing studies on genetic mutations and their impact on the tumor microenvironment, with a focus on mucin production and immune cell composition in colorectal cancer.  

2. **Data preparation**. Extract mutation data from TCGA and preprocess it for machine learning applications. Identify the best way to represent different mutation types for predictive modeling.  

3. **Machine learning**. Train models to predict mucin levels and immune cell composition based on mutation data. The objective is to determine which mutation types are most relevant for understanding tumor microenvironment characteristics.  

4. **Interpretation**. Analyze model outputs to identify key genetic features influencing mucin and immune cell levels. Validate findings by comparing predictions with existing research.

# TCGA-COAD slides
The diagnostic slide images from TCGA are quite large and stored in **SVS format**, which contains high-resolution pathology images. 

To analyse locally, I created a **subset of tumor slides**, converted them to PNG format, and uploaded them to Google Drive for easier access. You can download the subset from the following link:

[Download PNG subset](https://drive.google.com/file/d/1ZP-sRfEzg9YKTQu-9H6PNP3HyNNF2Bdk/view?usp=sharing)

## Downloading Diagnostic Slide Images from TCGA

### Step 1: Create a Cohort
1. Go to the [GDC Data Portal](https://portal.gdc.cancer.gov/).
2. Select **"Colorectal"** as the cancer type. This will create a new cohort.

![Creating a Cohort](img/screen1.png)

3. Save your cohort by clicking the save button as shown in the screenshots.

![Saving a Cohort](img/screen2.png)

### Step 2: Select Diagnostic Slide Images
1. Navigate to the [Repository](https://portal.gdc.cancer.gov/analysis_page?app=Downloads) page.
2. Ensure that you are working with the **Colorectal cohort**.
3. In the **Filters** section, locate the "Experimental Strategy" panel.
4. Select **"Diagnostic Slide"**.

![Saving a Cohort](img/screen3.png)

### Step 3: Add Files to Cart
1. Click **"Add All Files to Cart"** to add the selected images.
2. Navigate to your cart by clicking on the cart icon in the top-right corner.

### Step 4: Downloading Large Data
1. Since the dataset is large, it is recommended to use the **GDC Data Transfer Tool**.
2. Download the tool from [GDC Data Transfer Tool](https://gdc.cancer.gov/access-data/gdc-data-transfer-tool).
3. Follow the instructions provided by GDC to download your selected images efficiently.

