# Downloading Mutational Information from TCGA

## Overview
Mutational information from The Cancer Genome Atlas (TCGA) is stored in **Mutation Annotation Format (MAF)**. MAF files contain detailed information about somatic mutations, including single nucleotide variants (SNVs) and small insertions/deletions (indels).

For more information about the MAF format, refer to the official documentation: [GDC MAF Format](https://docs.gdc.cancer.gov/Data/File_Formats/MAF_Format/).

## Downloading MAF Files using TCGAbiolinks
The **TCGAbiolinks** R package provides an easy way to query and download MAF files from TCGA. Below is an example code snippet demonstrating how to download MAF data for **TCGA-COAD (Colon Adenocarcinoma)**.

### Code 
```r
# Define the cancer type
cancer <- "COAD"

# Construct the query for GDC (Genomic Data Commons)
query <- TCGAbiolinks::GDCquery(
  project = paste0("TCGA-", cancer),
  data.category = "Simple Nucleotide Variation",
  data.type = "Masked Somatic Mutation",
  workflow.type = "Aliquot Ensemble Somatic Variant Merging and Masking",
  access = "open"
)

# Download the data based on the query
TCGAbiolinks::GDCdownload(query)

# Prepare the MAF data from the downloaded files
maf <- TCGAbiolinks::GDCprepare(query)
```

### Barcode transformation 
To convert **Tumor_Sample_Barcode** to **case_submitter_id**, remove the suffix from the barcode.

Example:
  - **Tumor Sample Barcode**: `TCGA-A6-2671-01A-11D-A36X-10`
  - **Corresponding Case Submitter ID**: `TCGA-A6-2671`