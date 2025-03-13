# Table of contents

- [Mucin data](#mucin-data)
  - [Mucin data columns](#mucin-data-columns)
- [Mucin gene expression data](#mucin-gene-expression-data)
  - [Gene expression data](#gene-expression-data)
- [Clinical Data](#clinical-data)
  - [Sample id](#sample-id)
  - [Patient characteristics](#patient-characteristics)
  - [MSI and TMB](#msi-and-tmb)
  - [Tumor stage](#tumor-stage)
  - [Survival data](#survival-data)
  - [Immune cell estimation from blood](#immune-cell-estimation-from-blood)
  - [Tumor-infiltrating lymphocytes (TIL) estimation from images](#tumor-infiltrating-lymphocytes-til-estimation-from-images)
  - [Coverage](#coverage)
  - [Immune cell estimation from ESTIMATE algorithm](#immune-cell-estimation-from-estimate-algorithm)
- [Neoantigens from pVACseq](#neoantigens-from-pvacseq)

# Mucin data

Mucin data is taken from the study: 

Nguyen, Huu-Giao, et al. *"Image-based assessment of extracellular mucin-to-tumor area predicts consensus molecular subtypes (CMS) in colorectal cancer."* Modern Pathology 35.2 (2022): 240-248.

## Sample id
- **case_submitter_id**: A unique patient identifier that submitted the sample. It does not correspond to **Tumor_Sample_Barcode** used in other TCGA files. To understand more, refer to [GDC](https://docs.gdc.cancer.gov/Encyclopedia/pages/TCGA_Barcode/).
- **Transformation**: To convert **Tumor_Sample_Barcode** to **case_submitter_id**, remove the suffix from the barcode.
  - Example:
    - **Tumor Sample Barcode**: `TCGA-A6-2671-01A-11D-A36X-10`
    - **Corresponding Case Submitter ID**: `TCGA-A6-2671`

## Mucin data columns
- **MSI**: Microsatellite Instability (MSI) status of the sample. Possible values: `MSS` (Microsatellite Stable) or `MSI` (Microsatellite Instable).
- **average_mucin**: The average level of mucin detected in the sample.
- **max_mucin**: The maximum mucin level detected in the sample.
- **mucin**: A binary indicator (`0` or `1`), where `1` denotes the presence of mucin in the sample and `0` indicates its absence.
- **CMS**: Consensus Molecular Subtype (CMS) classification of colorectal cancer, with possible values: `CMS1`, `CMS2`, `CMS3`, or `CMS4`. 

# Mucin gene expression data

The `muc_tpm.csv` file contains gene expression data for mucin-associated genes. Expression values are represented in **Transcripts Per Million (TPM)**, which normalizes gene expression levels for comparison across samples.

## Sample id
- **sample_submitter_id**: A unique identifier for each sample, corresponding to **Tumor_Sample_Barcode** in TCGA datasets. More details on sample barcodes can be found in the [GDC documentation](https://docs.gdc.cancer.gov/Encyclopedia/pages/TCGA_Barcode/).

## Gene expression data
Each column (except `sample_submitter_id`) corresponds to a mucin-associated gene, with expression values given in TPM.

Examples of mucin genes included:
- **MUC1, MUC2, MUC4, MUC5AC, MUC5B, MUC6, MUC7** – well-known mucin genes involved in various biological processes, including tumor progression.
- **MUC12, MUC13, MUC15, MUC16, MUC17, MUC19, MUC20, MUC21, MUC22, MUC3A** – additional mucin genes implicated in colorectal cancer biology.
- **MUCL1, MUCL3** – mucin-like genes with lesser-known roles in CRC.

# Clinical data

## Sample id
- **Tumor_Sample_Barcode, case_submitter_id, sample_submitter_id**: These are unique codes assigned to each sample from the TCGA (The Cancer Genome Atlas) dataset. For more information look at [GDC](https://docs.gdc.cancer.gov/Encyclopedia/pages/TCGA_Barcode/)
- **dataset**: Specifies the type of TCGA dataset. Since COAD (colon adenocarcinoma) and READ (rectal adenocarcinoma) datasets are combined, this column tracks which dataset each sample belongs to.
- **sample_type**: Indicates the type of sample. TCGA includes different sample types such as normal solid tissue and primary tumor. Since we focus only on primary tumors, this column is mainly for verification.

## Patient characteristics
- **age**: The age of the patient at the time of diagnosis, represented as years to birth.
- **gender**: The gender of the patient.

## MSI and TMB
- **MSI_TMB**: A classification combining Microsatellite Instability (MSI) status and Tumor Mutational Burden (TMB). This classification includes:
  - "MSI-H" (Microsatellite Instability-High)
  - "MSS/TMB-H" (Microsatellite Stable with High Tumor Mutational Burden)
  - "MSS/TMB-L" (Microsatellite Stable with Low Tumor Mutational Burden)
  
  These are the three main groups studied in this research. For further details, refer to my draft (email me if you dont have access at xkdn@zhaw.ch).
- **MSI**: Provides specific information on the microsatellite instability status.
- **TMB**: Represents the tumor mutational burden, a measure of the number of mutations per megabase in the tumor genome.

## Tumor stage
- **pathologic_stage**: Overall classification of the cancer stage based on tumor size, lymph node involvement, and metastasis.
- **pathology_T_stage**: Specifies the size and extent of the primary tumor.
- **pathology_N_stage**: Indicates the involvement of nearby lymph nodes.
- **pathology_M_stage**: Describes whether the cancer has metastasized to distant parts of the body.

## Survival data
- **residual_tumor**: The amount of remaining tumor after surgery, categorized as R0 (no residual tumor), R1 (microscopic residual), or R2 (macroscopic residual).
- **overall_survival**: The time (in days) from diagnosis until death or last follow-up.
- **alive (OS)**: Binary indicator of patient survival status (1 = alive, 0 = deceased).

## Immune cell estimation from blood
These columns represent different types of immune cells measured in the tumor microenvironment:
- **lymphocytes**: A type of white blood cell crucial for the immune response.
- **neutrophils**: White blood cells involved in inflammation and response to infection.
- **eosinophils**: A type of white blood cell associated with allergic reactions and certain infections.
- **mast_cells**: Immune cells that play a role in allergic responses and inflammation.
- **dendritic_cells**: Antigen-presenting cells that help trigger immune responses.
- **macrophages**: Large immune cells that engulf and digest cellular debris and pathogens.

## Tumor-infiltrating lymphocytes (TIL) estimation from images
- **number_of_TIL_patches**: The count of TIL patches identified in tumor images.
- **number_of_clusters**: The number of immune cell clusters detected in the tumor.
- **til_percentage**: The estimated percentage of tumor-infiltrating lymphocytes based on image analysis.
- **leukocyte_fraction**: The fraction of leukocytes (white blood cells) present in the tumor microenvironment.
- **immune_subtype**: Classification of tumors based on immune cell composition and activity.
- **global_pattern**: A descriptor of immune infiltration patterns in tumor tissues.

Data is taken from this study:

Saltz, J., Gupta, R., Hou, L., Kurc, T., Singh, P., Nguyen, V., Samaras, D., Shroyer, K.R., Zhao, T., Batiste, R., et al.: Spatial organization and molecular correlation of tumor-infiltrating lymphocytes using deep learning on pathology images. Cell reports 23(1), 181–193 (2018)

## Coverage
- **mean_coverage**: The average depth of sequencing coverage across the genome.
- **proportion_coverage_30x**: The proportion of the genome covered at a minimum of 30x sequencing depth.

## Immune cell estimation from ESTIMATE algorithm
The ESTIMATE algorithm uses gene expression data to infer different tumor properties:
- **stromal**: Measures the presence of stromal cells in the tumor microenvironment.
- **immune**: Estimates the level of immune cell infiltration in the tumor.
- **estimate**: Overall score combining stromal and immune components.
- **purity**: An estimation of tumor purity, i.e., the proportion of cancer cells in the sample.

ESTIMATE algorithm paper:

Yoshihara, K., et al.: Inferring tumour purity and stromal and immune cell admix-ture from expression data. Nat Commun 4, 2612 (2013) https://doi.org/10.1038/ncomms3612


# Neoantigens from pVACseq

This dataset was generated using pVACseq, a tool that predicts neoantigens based on sequencing data. Neoantigens are mutations in tumor cells that can be recognized by the immune system and are crucial in immunotherapy response prediction.

- **Tumor_Sample_Barcode**: Unique identifier for each sample in the TCGA dataset.
- **variant_type**: Specifies the type of variant found in the neoantigen analysis. Include missense mutations, frameshift (FS) mutations and inframe deletion (inframe_del). An inframe deletion is a type of mutation where one or more codons (sets of three nucleotides) are deleted from the DNA sequence without disrupting the overall reading frame of the gene. .
- **neoantigens**: The number of neoantigens detected for each variant type in the sample.



