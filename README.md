# Bandgap ML Teaching Module

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Shlok-Joseph-Paul/bandgap-ml-teaching-module/blob/main/notebooks/01_predicting_bandgaps_student.ipynb)

This repository contains a beginner-friendly materials informatics module for predicting experimental semiconductor band gaps from chemical formula. It is designed for advanced undergraduate chemistry, materials science, and related courses that want a hands-on introduction to machine learning with chemically meaningful descriptors.

Students work through a Jupyter notebook that uses:

- `pandas`
- `numpy`
- `matplotlib`
- `scikit-learn`
- `pymatgen`
- `matminer`

The notebook guides students through loading experimental materials data, parsing chemical formulas, generating composition descriptors, training regression models, evaluating predictions, and reflecting on model limitations.

## Student quick start

1. Click the **Open in Colab** badge.
2. Run the setup cell.
3. Choose **Runtime -> Run all**.
4. Work through the notebook.
5. Answer the questions in `teaching_materials/student_worksheet.md`.

No local Python installation is required.

## Instructor materials

- Student notebook: `notebooks/01_predicting_bandgaps_student.ipynb`
- Student worksheet: `teaching_materials/student_worksheet.md`
- Instructor guide: `teaching_materials/instructor_guide.md`
- Manuscript outline: `manuscript/manuscript_outline.md`
- Generated figures: `figures/`

## What Students Will Do

Students will:

- load a public `matminer` dataset of experimental band gaps,
- inspect formulas such as Si, GaAs, TiO2, PbS, CdTe, and CsPbBr3,
- convert formulas into `pymatgen` `Composition` objects,
- generate Magpie composition features with `matminer`,
- train a `DummyRegressor` baseline model,
- train a `RandomForestRegressor` model,
- evaluate models using MAE and R2,
- create a predicted-vs-actual band gap plot,
- create a feature-importance plot,
- identify the largest model errors, and
- discuss chemistry, data quality, and model limitations.

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

## Run Locally

Google Colab is the recommended route for students. To run the notebook locally instead, create and activate a Python environment:

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

Then open `notebooks/01_predicting_bandgaps_student.ipynb` and run the cells in order.

## Dataset

The notebook uses the `matbench_expt_gap` dataset available through `matminer.datasets.load_dataset`. This dataset contains experimentally measured band gaps paired with chemical compositions.

Students should treat the dataset as real scientific data: useful, imperfect, and shaped by measurement conditions, reporting choices, and the limits of composition-only representations.

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
