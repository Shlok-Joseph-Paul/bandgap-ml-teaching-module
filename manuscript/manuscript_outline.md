# Manuscript Outline: Teaching Experimental Band Gap Prediction with Materials Informatics

## Working Title

Predicting Semiconductor Band Gaps from Chemical Formula: A Beginner-Friendly Materials Informatics Module for Advanced Undergraduate Students

## Target Venues

- *Journal of Chemical Education*
- *Digital Discovery*
- *Materials Advances*
- discipline-specific chemical education or materials education venues

## Abstract

Briefly describe the educational need, the module design, the public dataset, the Python workflow, and the intended learning outcomes. Emphasize that students learn both practical machine learning skills and critical interpretation of model limitations.

## 1. Introduction

- Motivation for data-driven materials discovery.
- Importance of semiconductor band gaps in photovoltaics, LEDs, photocatalysis, detectors, and electronics.
- Need for classroom materials that connect chemistry, materials descriptors, and machine learning.
- Why formula-based prediction is a useful entry point.
- Learning goals and audience.

## 2. Educational Context

- Course level and prerequisites.
- Possible placements in physical chemistry, inorganic chemistry, materials chemistry, computational chemistry, or materials science courses.
- Expected time commitment.
- Relationship to broader scientific computing or data literacy outcomes.

## 3. Dataset and Scientific Background

- Source of experimental band gap data through matminer.
- Meaning of the target variable in electronvolts.
- Examples used in the module: Si, GaAs, TiO2, PbS, CdTe, CsPbBr3.
- Scientific limitations of composition-only data:
  - polymorphism,
  - crystal structure,
  - defects and stoichiometry deviations,
  - temperature,
  - measurement method,
  - direct versus indirect gaps,
  - literature variability.

## 4. Computational Workflow

- Loading and inspecting the dataset with `pandas`.
- Parsing formulas using `pymatgen`.
- Generating composition descriptors with `matminer`.
- Splitting data into training and test sets.
- Training a naive baseline model.
- Training a random forest model.
- Evaluating MAE and R2.
- Creating predicted-vs-actual and feature-importance plots.
- Identifying and discussing large prediction errors.

## 5. Pedagogical Design

- Beginner-friendly notebook structure.
- Frequent code comments and reflection prompts.
- Emphasis on model comparison rather than model worship.
- Connection between descriptors and chemical intuition.
- Error analysis as a route to scientific reasoning.

## 6. Assessment Strategy

- Pre-lab conceptual questions.
- Notebook completion checks.
- Plot interpretation questions.
- Short written explanation of a large model error.
- Reflection on missing information and model limitations.
- Optional rubric for computational correctness, chemical reasoning, and critical interpretation.

## 7. Results from Classroom or Pilot Use

Possible data to collect:

- student completion rates,
- pre/post confidence with Python and machine learning,
- quality of written explanations,
- common misconceptions,
- timing observations,
- student feedback on difficulty and relevance.

If classroom data are not yet available, this section can be framed as a planned evaluation.

## 8. Discussion

- Strengths of the module:
  - uses real public data,
  - connects chemical formula to numerical descriptors,
  - produces interpretable visual outputs,
  - supports discussion of uncertainty and limitations.
- Challenges:
  - dependency installation,
  - featurization time,
  - possible overinterpretation of feature importance,
  - variability in student Python background.
- Adaptations for different course levels.

## 9. Conclusions

- Summarize how the module introduces materials informatics through a chemically meaningful prediction task.
- Reiterate that predictive performance must be interpreted alongside domain knowledge.
- Point toward extensions involving structure-aware models, uncertainty quantification, and materials screening.

## Supporting Information

- Student notebook.
- Student worksheet.
- Instructor guide.
- Environment or requirements file.
- Example figures.

## Potential References

- Ward, L. et al. "Matminer: An open source toolkit for materials data mining." *Computational Materials Science* 152, 60-69 (2018).
- Dunn, A. et al. "Benchmarking Materials Property Prediction Methods: The Matbench Test Set and Automatminer Reference Algorithm." *npj Computational Materials* 6, 138 (2020).
- Zhuo, Y., Mansouri Tehrani, A., and Brgoch, J. "Predicting the Band Gaps of Inorganic Solids by Machine Learning." *The Journal of Physical Chemistry Letters* 9, 1668-1673 (2018).
- Additional references on semiconductor band gaps, materials informatics pedagogy, and descriptor-based machine learning.
