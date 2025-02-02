# Plot projected PCs

Once `project_pc.sh` finished, please run `Rscript plot_projected_pc.R` to plot all the projected PCs. This script also generates a text file containing per-sample projected PCs **without including biobank-specific individual IDs**.

If PLINK2 was used to project pcs please revise the header of the .sscore file by changing "PC1_SUM" to "PC1",  "PC2_SUM" to "PC2", etc. 

## Required packages

To run the script, please install the following packages.

```
install.packages(c("data.table", "hexbin", "optparse", "patchwork", "R.utils", "tidyverse"))
```

## Available options

```
Rscript plot_projected_pc.R \
  --sscore [path to .sscore output] \
  --phenotype-file [path to phenotype file] \
  --phenotype-col [phenotype column name] \
  --covariate-file [path to covariate file] \
  --pc-prefix [prefix of PC columns: default "PC"] \
  --pc-num [number of PCs used in GWAS] \
  --ancestry [ancestry code: AFR, AMR, EAS, EUR, MID, or SAS] \
  --study [your study name] \
  --out [output name prefix]
```

Ancestry codes for `--ancestry` are:

- African (AFR)
- Admixed American (AMR)
- East Asian (EAS)
- European (EUR)
- Middle Eastern (MID)
- South Asian (SAS)

If your cohort contains multiple ancestries, please use `--ancestry-file` and `--ancestry-col` to specify for each individual.

```
  --ancestry-file [path to ancestry file] \
  --ancestry-col [ancestry column name]
```

If your cohort submits multiple analyses, please run the script with different `--phenotype-col`. It will automatically excludes samples without case/control status.

If your system doesn't have access to the Internet, please download a reference score file [here](https://storage.googleapis.com/gbmi-public/hgdp_tgp_pca_gbmi_snps_scores.txt.bgz) and specify it via `--reference-score-file`.

## Upload

Please upload all the `.png` files and `.projected.pca.tsv.gz` file to the google bucket of your biobank. Detailed instruction can be found **[https://docs.google.com/document/d/1nLe4o0nZ9DOzZufuYlHZuU3VBiHGC3rcJgMBkjpeHIk/edit?usp=sharing]** and the google bucket information can be found **https://docs.google.com/spreadsheets/d/1dO4J_zzvRY37ErStS1VVcZfJvkz-6WOJ7sqOZfvtl-c/edit?usp=sharing**
