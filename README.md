# Bandgap ML Teaching Module

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Shlok-Joseph-Paul/bandgap-ml-teaching-module/blob/main/notebooks/01_predicting_bandgaps_student.ipynb)

This repository contains a beginner-friendly materials informatics module for predicting experimental semiconductor band gaps from chemical formula. It is designed for advanced undergraduate chemistry, materials science, and related courses that want a hands-on introduction to machine learning with chemically meaningful descriptors.

Students work through a Jupyter notebook that uses `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `pymatgen`, and `matminer` to:

- load a public matminer dataset of experimental band gaps,
- parse chemical formulas into `pymatgen` `Composition` objects,
- convert formulas into numerical composition descriptors,
- train a naive baseline model and a random forest model,
- evaluate model performance using MAE and R2,
- visualize predicted vs. actual band gaps,
- interpret feature importances,
- inspect the largest model errors, and
- reflect on chemistry, data quality, and model limitations.

## Repository Structure

```text
bandgap-ml-teaching-module/
|-- README.md
|-- requirements.txt
|-- notebooks/
|   `-- 01_predicting_bandgaps_student.ipynb
|-- figures/
|   `-- .gitkeep
|-- teaching_materials/
|   |-- student_worksheet.md
|   `-- instructor_guide.md
`-- manuscript/
    `-- manuscript_outline.md
```

## Quick Start

### Run Online with Google Colab

Click the **Open in Colab** badge at the top of this README to run the notebook online without installing Python locally. The notebook includes a setup cell that installs the required packages when it detects Google Colab.

Note: this repository is currently private. Students will need access to the GitHub repository, or the repository should be made public, for the Colab badge to open smoothly.

### Run Locally

Create and activate a Python environment, then install the required packages:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

Launch Jupyter:

```bash
jupyter lab
```

Open `notebooks/01_predicting_bandgaps_student.ipynb` and run the cells in order.

## Dataset

The notebook uses the `matbench_expt_gap` dataset available through `matminer.datasets.load_dataset`. This dataset contains experimentally measured band gaps paired with chemical compositions. Students should treat it as a real scientific dataset: useful, imperfect, and shaped by measurement conditions, reporting choices, and the limits of composition-only representations.

## Learning Goals

By the end of the module, students should be able to:

- explain why chemical formulas must be converted into numerical features before they can be used in most machine learning models,
- use `pymatgen` to parse and inspect chemical compositions,
- use `matminer` to calculate composition-based descriptors,
- train and compare simple regression models,
- interpret MAE and R2 in the context of band gap prediction,
- identify examples where model predictions are poor, and
- connect model errors to chemistry, missing structural information, and dataset limitations.

## Suggested Use

This module works well as a 75 to 120 minute guided lab, a flipped-classroom activity, or a short computational assignment. The notebook is intentionally written with many comments so students can focus on concepts rather than syntax alone.

## References

- Ward, L. et al. "Matminer: An open source toolkit for materials data mining." *Computational Materials Science* 152, 60-69 (2018).
- Dunn, A. et al. "Benchmarking Materials Property Prediction Methods: The Matbench Test Set and Automatminer Reference Algorithm." *npj Computational Materials* 6, 138 (2020).
- Zhuo, Y., Mansouri Tehrani, A., and Brgoch, J. "Predicting the Band Gaps of Inorganic Solids by Machine Learning." *The Journal of Physical Chemistry Letters* 9, 1668-1673 (2018).
