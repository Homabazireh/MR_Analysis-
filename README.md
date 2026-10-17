# MR analysis

Anonymised R Markdown code for bidirectional Mendelian randomisation of
circulating proteins and kidney function (eGFRcrea and eGFRcys).

## Contents

- `MR_analysis.Rmd`: the supplied analysis notebook, with personal details and
  embedded credentials removed.
- `.Renviron.example`: empty local configuration template.
- `.gitignore`: excludes local credentials, source data, cached objects, and
  generated results from version control.

The notebook contains forward and reverse MR, IVW, weighted-median and MR-Egger
analyses, sensitivity analyses, MR-PRESSO, forest plots, and F-statistics.
Figure files are excluded from this package.

## Local setup

1. Open R or RStudio in the repository directory.
2. Provide the required R packages: `TwoSampleMR`, `data.table`, `dplyr`,
   `tibble`, `readxl`, `stringr`, `ieugwasr`, `ggplot2`, `tidyr`, `MRPRESSO`,
   `knitr`, and `rmarkdown`. Some existing notebook sections use `remotes` to
   install MR-PRESSO. Package versions were not supplied or pinned.
3. Supply the analysis inputs locally. The default input directory is `data/`.
   The notebook expects deCODE pQTL `.txt.gz` files,
   `metal_eGFR_meta_ea1.TBL.map.annot.gc.gz`,
   `metal_eGFRcys_meta1.TBL.map.annot.gc.gz`, and, for the workbook-based forest
   plots, `MR_Results.xlsx`. These files are not included.
4. Set `OPENGWAS_JWT` outside the notebook. One option is to copy
   `.Renviron.example` to `.Renviron`, enter a newly issued token in that local
   file, and restart R from the repository directory. `.Renviron` is ignored
   by Git. Do not put a real token into the example file or notebook.
5. Run the `local-configuration` chunk first, then the relevant analysis
   sections in order. Relative analysis outputs and intermediate files use
   `results/`. Publication forest plots use `results/forest_plots/`.

Optional environment variables allow local paths to be configured without
editing the notebook:

| Variable | Default |
| --- | --- |
| `MR_PROJECT_DIR` | Directory from which the setup chunk starts |
| `MR_DATA_DIR` | `<project>/data` |
| `MR_RESULTS_DIR` | `<project>/results` |
| `MR_RESULTS_WORKBOOK` | `<data>/MR_Results.xlsx` |

Use absolute paths for overrides. Keep personal paths in local configuration.

## Execution status

This is an anonymised research notebook. Its repeated and alternative analysis
sections, statistical methods, thresholds, and supplied scientific results
have been retained. It is not a newly validated end-to-end pipeline.

Existing sections load cached objects, including `decode_pqtl.RData` in the
input directory and `pqtl_sig.RData` in the results directory. They also load
harmonised objects produced in earlier sections. These objects were not
supplied. Review the alternative sections and provide or generate the required
objects before running the notebook from start to finish.

The analysis was not executed during anonymisation because R and the source
datasets were unavailable. Static checks verified the removal of the detected
identifiers and credentials.

## The dataset

Required pqtl from the decode study and the eGFR data from the CKDGen study were downloaded. 
