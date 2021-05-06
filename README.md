#  Mapping IRAK4, PUS7L, and ANRIL genetic variation, DNA methylation, and expression in atherosclerotic plaques.

<!-- Please add a brief introduction to explain what the project is about    -->

_Project ID_: `AE_171212_GBASATEMUR_ZMALLAT`.

_Collaborators_: Gemma Basatemur, Ziad Mallat.

# Background

In the past decade genome-wide association studies (GWAS) have robustly linked common genetic variation to _coronary artery disease (CAD)_, and identified 9p21 as a locus causally involved in CAD risk.

In this project we aim to map genetic variation at 9p21 (rs1333049) to _IRAK4_ DNA methylation (DNAm), and expression in atherosclerotic plaques. 

We associate the known risk loci to plaque-derived DNAm. We will associate overall plaque expression with plaque phenotypes using the bulk RNAseq data. 

## Methods

### General

We will use data from the Athero-Express Biobank Study. We have bulk RNAseq (n = 635 samples), genome-wide methylation (Illumina 450K) in n ± 600, as well as overlapping genetic data for ±2,100 individuals with extensive histological plaque characterisation. We will address the following questions:

- Gene expression correlated to characteristics of plaques?
- Is 9p21 associated to DNAm?
- Are DNA methylation and gene expression correlated?


### Analyses

#### Modeling gene variation to plaque phenotypes

For the genetic analyses we will perform regression analyses adjusted for age, sex (where applicable), hospital and genetic principal components. 

    model 1: `phenotype ~ age + sex + Hospital + PC1 + PC2 + PC3 + PC4`
    
Plaque phenotypes (characteristics) are:

- `calcification`, coded `Calc.bin` no/minor vs. moderate/heavy staining
- `collagen`, coded `Collagen.bin` no/minor vs. moderate/heavy staining
- `fat10`, coded `Fat.bin_10` no/<10% fat vs. >10% fat
- `fat40`, coded `Fat.bin_40` no/<40% fat vs. >40% fat
- `intraplaque hemorrhage`, coded `IPH.bin` no vs. yes
- `macrophages (CD68)`, coded `macmean0` mean of computer-assisted calculation CD68<sup>+</sup> region of interest
- `smooth muscle cells (alpha-actin)`, coded `smcmean0` mean of computer-assisted calculation SMA<sup>+</sup> region of interest
- `intraplaque vessel density (CD34)`, coded `vessel_density` manually counted CD34<sup>+</sup> cells per 3-4 hotspots
- `mast cells`, coded `Mast_cells_plaque` manually counted mast cell tryptase<sup>+</sup> cells (https://academic.oup.com/eurheartj/article/34/48/3699/484981)
- `neutrophils (CD66b)`, coded `neutrophils` manually counted CD66b<sup>+</sup> cells (https://pubmed.ncbi.nlm.nih.gov/20595650/)

Continuous variables were inverse-rank normal transformated, indicated by `_rankNorm`. 


#### Modeling SNP to plaque gene expression and DNA methylation

For this molecular quantitative trait locus (molQTL) we performed regression analyses adjusted for covariates as follows.

    model 1: `phenotype ~ SNP + Age + Sex + Gen. PC 1 + Gen. PC 2 + Gen. PC 3 + Gen. PC 4 + Hospital


#### Associate gene expression to plaque phenotypes

Associate bulk gene expression with plaque characteristics. 


#### Associate gene expression to methylation

    model 1: `phenotype ~ age + sex + Hospital`
    model 2: `phenotype ~ age + sex + Hospital + BMI + GFR_MDRD + hypertension + diabetes + lipid-lowering drugs`


## Where do I start?

You can load this project in RStudio by opening the file called 'AE_171212_9p21_IRAK4.Rproj'.

## Project structure

<!--  You can add rows to this table, using "|" to separate columns.         -->
File                       | Description                         | Usage         
-------------------------- | ----------------------------------- | --------------
README.md                  | Description of project              | Human editable
AE_171212_9p21_IRAK4.Rproj | Project file                        | Loads project 
LICENSE                    | User permissions                    | Read only     
.worcs                     | WORCS metadata YAML                 | Read only     
renv.lock                  | Reproducible R environment          | Read only     
Results                    | Some results                        | Read only     

<!--  You can consider adding the following to this file:                    -->
<!--  * A citation reference for your project                                -->
<!--  * Contact information for questions/comments                           -->
<!--  * How people can offer to contribute to the project                    -->
<!--  * A contributor code of conduct, https://www.contributor-covenant.org/ -->

# Reproducibility

This project uses the Workflow for Open Reproducible Code in Science (WORCS) to
ensure transparency and reproducibility. The workflow is designed to meet the
principles of Open Science throughout a research project. 

To learn how WORCS helps researchers meet the TOP-guidelines and FAIR principles,
read the preprint at https://osf.io/zcvbs/

## WORCS: Advice for authors

* To get started with `worcs`, see the [setup vignette](https://cjvanlissa.github.io/worcs/articles/setup.html)
* For detailed information about the steps of the WORCS workflow, see the [workflow vignette](https://cjvanlissa.github.io/worcs/articles/workflow.html)

## WORCS: Advice for readers

Please refer to the vignette on [reproducing a WORCS project]() for step by step advice.
<!-- If your project deviates from the steps outlined in the vignette on     -->
<!-- reproducing a WORCS project, please provide your own advice for         -->
<!-- readers here.                                                           -->

# Acknowledgements

Dr Sander W. van der Laan is funded through grants from the Netherlands CardioVascular Research Initiative of the Netherlands Heart Foundation (CVON 2011/B019 and CVON 2017-20: Generating the best evidence-based pharmaceutical targets for atherosclerosis [GENIUS I&II]). We are thankful for the support of the ERA-CVD program ‘druggable-MI-targets’ (grant number: 01KL1802), the EU H2020 TO_AITION (grant number: 848146), and the Leducq Fondation ‘PlaqOmics’.

Plaque samples are derived from carotid endarterectomies as part of the [Athero-Express Biobank Study](http:www/atheroexpress.nl) which is an ongoing study in the UMC Utrecht.

The framework was based on the [`WORCS` package](https://osf.io/zcvbs/).

<a href='https://www.era-cvd.eu'><img src='images/ERA_CVD_Logo_CMYK.png' align="center" height="75" /></a> <a href='https://www.plaqomics.com'><img src='images/leducq-logo-large.png' align="center" height="75" /></a> <a href='https://www.fondationleducq.org'><img src='images/leducq-logo-small.png' align="center" height="75" /></a> <a href='https://osf.io/zcvbs/'><img src='images/worcs_icon.png' align="center" height="75" /></a>

#### Changes log
    
    _Version:_      v1.0.2</br>
    _Last update:_  2021-05-06</br>
    _Written by:_   Sander W. van der Laan (s.w.vanderlaan-2[at]umcutrecht.nl).
    
    * v1.0.2 Added all relevant files. 
    * v1.0.0 Initial version. 

--------------

#### Creative Commons BY-NC-ND 4.0
##### Copyright (c) 1979-2021 Sander W. van der Laan | s.w.vanderlaan [at] gmail [dot] com.

This is a human-readable summary of (and not a substitute for) the [license](LICENSE). 

You are free to: 
Share — copy and redistribute the material in any medium or format. The licensor cannot revoke these freedoms as long as you follow the license terms.

Under the following terms: 
- Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use. 
- NonCommercial — You may not use the material for commercial purposes. 
- NoDerivatives — If you remix, transform, or build upon the material, you may not distribute the modified material. 
- No additional restrictions — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

Notices: 
You do not have to comply with the license for elements of the material in the public domain or where your use is permitted by an applicable exception or limitation.
No warranties are given. The license may not give you all of the permissions necessary for your intended use. For example, other rights such as publicity, privacy, or moral rights may limit how you use the material.


