# Exploratory Gene Expression Analysis

Exploratory analysis of gene-expression patterns in smokers and
non-smokers using Python, descriptive statistics, and data visualisation.

## Overview

This project reads a prepared gene-expression CSV, organises samples by
group, calculates feature-level summary statistics, and visualises
differences in expression patterns.

The notebook references GEO dataset GDS3713, "Smoking effect on
B lymphocytes in females."

The analysis is educational and exploratory. It is not a clinically
validated tool or a formal differential-expression testing pipeline.

## Analysis workflow

1. Read expression values and group labels from a CSV.
2. Organise samples in nested Python dictionaries.
3. Calculate mean, variance, and standard deviation for each feature
   within each group.
4. Visualise features with the largest absolute differences in mean
   expression.
5. Identify features with the greatest variance among smokers.
6. Calculate log2 ratios of group means.
7. Display fold-change and sample-level expression heatmaps.

## Repository contents

- `Gene_Expression_Analysis_Project.ipynb`: analysis notebook.
- `requirements.txt`: Python dependencies.
- `data/GDS3713-small.csv`: input dataset containing 79 samples and
  3,000 expression features.
- `data/README.md`: dataset source, publication citation, course
  provenance, CSV layout, and data-handling notes.
- `.gitignore`: rules for excluding local and temporary files from
  version control.

## Data availability

The input file is included as `data/GDS3713-small.csv`.

It contains 79 samples: 40 controls and 39 smokers, with 3,000
expression features per sample.

In Google Colab, upload this CSV when prompted. For local execution,
leave it in the `data/` directory and run the notebook from the
repository's root directory.

See [the data documentation](data/README.md) for the original study
citation, the source of the teaching subset, and the expected CSV layout.

The original GEO download is not a direct replacement for this specific
input file: the notebook expects the supplied feature subset and layout.

## Run in Google Colab

1. Open Google Colab.
2. Choose File > Open notebook > GitHub.
3. Search for this repository and open
   `Gene_Expression_Analysis_Project.ipynb`.
4. Run the notebook from the first cell.
5. Upload the prepared `**GDS3713-small.csv**` when prompted.
6. Run the remaining cells in order.

If a required package is unavailable, install the packages listed in
`requirements.txt`.

## Run locally

Download or clone this repository, then open a terminal in its root
directory.

Install the dependencies and start JupyterLab:

```bash
python -m pip install -r requirements.txt
python -m jupyterlab
```

Keep the included CSV at `data/GDS3713-small.csv`. Open
`Gene_Expression_Analysis_Project.ipynb` in JupyterLab and run the cells
in order.

## Limitations

- Descriptive analysis only; no hypothesis testing or multiple-testing
  correction.
- No adjustment for potential confounding variables.
- Fold-change interpretation depends on the input expression scale.
- Variance and standard deviation use `**ddof=0**`.
- The sample-level heatmap shows a limited number of samples per group
  and does not perform clustering.
- The procedure used to select the supplied 3,000-feature subset is
  not documented in this repository.
- Dependency versions are not pinned to a tested environment.

## Project context

This project was originally developed as a three-person group assignment
for Fondamenti di Informatica at the University of Pavia, Italy.

The project explored gene-expression patterns in smokers and non-smokers
through Python-based data processing, descriptive statistics, and
visualisation.

I subsequently reorganised and revised the notebook for this repository.
The original contributions and later changes are described below.

## Authors and contributions

### Original project contributors
- Agata Anna Sawicka
- Alfonso De Caro
- Enrico Tognini

### My original contribution

As a repository maintainer, I wrote `log2_fold_change_heatmap()` and `expression_heatmap()`,
including the calculation and ranking of log2 fold changes, the
annotated fold-change heatmap, and the sample-level expression heatmap
with smoking-group annotations.

The other group members contributed the original data-loading code,
group-level descriptive statistics, mean-difference bar chart, and
ranking of features by variance among smokers.

### Subsequent revisions

I restructured and prepared the notebook for publication in this
repository. This included:

- Organising the workflow into separate sections for data loading,
  descriptive statistics, mean-expression differences, within-group
  variability, and heatmap visualisation.
- Revising the CSV-loading function to match the supplied file layout.
- Adding input checks for row lengths and sample-group labels.
- Replacing extensive debugging output with a concise dataset summary.
- Standardising plotting imports and updating function names and labels
  for consistency.
- Writing the repository documentation and data-format instructions.

These revisions build on the original collaborative work.

## Possible extensions

- Check for duplicate feature names and provide more informative
  errors for invalid expression values.
- Record the tested Python and package versions.
- Add optional export of summary tables and figures.
- Document or reproduce the feature-subset selection procedure,
  if the necessary source information becomes available.
