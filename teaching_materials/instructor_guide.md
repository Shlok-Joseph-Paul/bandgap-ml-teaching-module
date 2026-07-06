# Instructor Guide: Bandgap ML Teaching Module

## Audience

This module is intended for advanced undergraduate chemistry, materials science, chemical engineering, or physics students. It assumes students have seen Python basics or have enough support to run and lightly modify a commented notebook.

## Estimated Time

- Short guided version: 75 minutes
- Standard lab version: 100 to 120 minutes
- Extended assignment with written reflection: one lab period plus homework

## Prerequisites

Students should have basic familiarity with:

- chemical formulas and stoichiometry,
- the concept of electronic band gaps,
- Python variables, functions, and tables,
- scatter plots, and
- the idea of train/test splits.

No prior machine learning experience is required.

## Preparation

Before class:

1. Clone or distribute this repository.
2. Create a fresh environment and run `pip install -r requirements.txt`.
3. Open the notebook and run it once to confirm that matminer can download or access the dataset.
4. Decide whether students will use the full dataset or a smaller sample for speed.
5. Confirm that students can save figures into the `figures/` directory.

If internet access is unreliable, run the notebook once on each teaching machine or provide a pre-downloaded version of the dataset according to your institution's data policies.

## Learning Objectives

After completing the activity, students should be able to:

- distinguish formulas, compositions, features, and targets,
- explain why descriptors are needed for many machine learning models,
- calculate composition descriptors using matminer,
- compare baseline and random forest regression performance,
- interpret MAE and R2 in a materials context,
- identify model failures, and
- critique the limits of composition-only prediction.

## Suggested Class Flow

### Opening Discussion: 10 minutes

Ask students:

- What controls a semiconductor band gap?
- Is formula alone enough to know a band gap?
- What information is lost when a material is represented only by composition?

Use Si, GaAs, TiO2, PbS, CdTe, and CsPbBr3 as familiar anchors.

### Notebook Work: 55 to 80 minutes

Recommended pacing:

1. Dataset loading and inspection: 10 minutes
2. Formula parsing with `pymatgen`: 10 minutes
3. Descriptor generation with `matminer`: 15 to 25 minutes
4. Baseline and random forest training: 15 minutes
5. Plot interpretation and error analysis: 15 to 20 minutes

### Wrap-Up: 10 to 20 minutes

Discuss:

- whether the random forest improves over the naive baseline,
- which features appear important,
- why the largest errors might be chemically interesting,
- how structure, phase, defects, temperature, or measurement method could change the target value, and
- what ethical or practical caution is needed when screening materials computationally.

### Optional Extension: 30 to 60 minutes

The notebook includes an optional extension on edge-case analysis, chemical-family error trends, gradient boosting, and permutation importance. This extension works well for a longer class period, a recitation, or homework after students complete the main notebook.

Use the extension when you want students to:

- compare the random forest with a more flexible tree-based model,
- ask whether error is distributed evenly across chemical families,
- distinguish built-in feature importance from permutation importance,
- connect large model errors to missing chemistry and structure, and
- think about why composition-only prediction is especially limited for quantum dots and nanocrystals.

For a shorter class, you can skip the gradient boosting and permutation importance sections and use only the edge-case clinic as a discussion prompt.

## Expected Outcomes

Exact numerical results may vary with package versions and random seeds, but students should usually observe:

- the random forest outperforming the mean-prediction baseline,
- nonzero scatter around the parity line in the predicted-vs-actual plot,
- larger errors for some chemically complex or underrepresented compositions,
- feature importances that often include elemental property statistics from the Magpie preset, and
- clear evidence that composition-only descriptors are useful but incomplete.

## Instructor Explanation Notes

Use these short explanations when introducing or debriefing the major concepts.

- `pymatgen`: Explain that a formula string is just text until it is parsed. `pymatgen` turns formulas such as `CsPbBr3` into composition objects that know the elements and stoichiometric ratios.
- `matminer`: Explain that `matminer` connects materials objects to machine learning by calculating descriptors from compositions, structures, or other materials data.
- Featurization: Emphasize that most machine-learning models need numerical inputs. Featurization is the translation from chemical representation to numerical descriptor table.
- Baseline model: Present the baseline as a sanity check. If a complex model cannot beat average-band-gap prediction, it has not learned useful structure-property patterns.
- Random forest: Describe it as many decision trees voting or averaging together. It is useful for nonlinear patterns but does not automatically understand physics.
- Gradient boosting: Contrast it with random forests. Boosting builds trees sequentially to correct earlier mistakes, which may improve accuracy but can still miss chemistry absent from the features.
- MAE/R2: MAE has the same units as the target, so students can interpret it directly in eV. R2 is a relative score compared with average prediction; negative values are possible for poor models.
- Parity plot: The diagonal is perfect prediction. Distance from the line is visual error. Systematic overprediction or underprediction can reveal model bias.
- Feature importance: Feature importance identifies descriptors the model used, not necessarily physical causes. Correlated features and hidden variables can complicate interpretation.
- Edge-case analysis: The worst predictions are useful teaching examples because they expose missing information such as structure, polymorph, defects, processing, sample size, or measurement conditions.

## Teaching Magpie Descriptors

Use the Magpie descriptor section to slow students down before they treat feature names as opaque model inputs.

- Emphasize that Magpie features are elemental-property summaries, not direct electronic-structure calculations.
- Point out that each feature name combines a statistic and an elemental property, such as `mean Electronegativity` or `range CovalentRadius`.
- Use `PbS` as a conceptual example: Pb and S differ in electronegativity, atomic size, atomic weight, and valence-electron patterns, all of which may correlate with band gap trends.
- Ask students to distinguish a chemically meaningful descriptor from a causal explanation. A useful predictor is not automatically the physical reason for a band gap.
- The feature explorer works well as a five-minute pair activity before the modeling section or as preparation for the interactive challenge.
- For discussion, compare oxides, chalcogenides, halides, and heavy-element semiconductors. Students should connect descriptor values to bonding, periodic trends, and missing structural information.
- Remind students that some Magpie properties, such as `GSbandgap`, `GSmagmom`, and `SpaceGroupNumber`, describe elemental reference states rather than the compound itself.

## Interactive Challenge Notes

Suggested timing: 20 to 30 minutes.

Suggested format: pairs or small groups. Each group should choose one target family, such as oxides, chalcogenides, halides, or pnictides, and try to improve that family-specific error while watching what happens to the overall MAE.

Suggested class activity:

1. Ask each group to write a chemistry-based hypothesis before touching the widgets.
2. Have each group run at least three experiments: one chemistry-guided, one automatic top-k, and one all-feature comparison.
3. Ask groups to record overall MAE, family MAE, selected features, and one remaining difficult material.
4. Close with a short report-out comparing overall MAE and family-specific MAE.

Warnings to emphasize:

- Students may overfit their choices to one train/test split even though the split is fixed for fair comparison.
- Feature importance and automatic feature selection can identify useful predictors, but useful predictors are not automatically physical causes.
- A reduced-feature model that performs slightly worse may still be scientifically valuable if it is easier to interpret.
- A more accurate model is not always the best scientific explanation.

Discussion prompts:

- When did chemistry intuition help, and when did it fail?
- Is the best predictive model always the best scientific explanation?
- Which families were easiest or hardest to improve?
- What missing information would you want next: structure, processing, defects, dimensionality, measurement details, or sample size?

Optional leaderboard activity:

- Compare group results by overall MAE.
- Compare group results by selected-family MAE.
- Ask whether the same experiment wins both leaderboards.

## Common Issues and Fixes

### matminer cannot load the dataset

Check internet access and package installation. Reinstall with:

```bash
python -m pip install --upgrade matminer pymatgen
```

If the dataset name changes in a future matminer release, inspect available datasets:

```python
from matminer.datasets import get_available_datasets
get_available_datasets()
```

### Featurization is slow

For a shorter in-class run, students can set `MAX_ROWS` in the notebook to a smaller number such as `1500`. Emphasize that this speeds computation but may change model performance.

### Some descriptors contain missing values

This is expected. The notebook drops rows with missing target values or failed Magpie featurization so the beginner workflow uses a clean numerical feature table. In a more advanced course, you can discuss imputation as an alternative.

### Students overinterpret feature importance

Remind students that random forest feature importances are model-specific and can be biased toward correlated or high-variance features. They are clues, not mechanistic proof.

## Assessment Ideas

Use any combination of:

- completed notebook,
- selected worksheet responses,
- short interpretation of the predicted-vs-actual plot,
- explanation of one large model error,
- one paragraph proposing a model improvement, or
- a brief comparison of composition-only and structure-aware approaches.

For a more formal assignment, use `teaching_materials/assessment_rubric.md`. For sample responses and grading calibration, use `teaching_materials/instructor_answer_key.md`.

## Extension Activities

- Use the included optional extension for a longer class or homework assignment.
- Replace the random forest with ridge regression, gradient boosting, or k-nearest neighbors.
- Compare performance using only simple stoichiometric features versus the full matminer feature set.
- Use cross-validation instead of a single train/test split.
- Add uncertainty estimates using repeated train/test splits.
- Compare experimental band gaps with computed band gaps from another dataset.
- Ask students to research one high-error compound and report possible polymorphs or measurement complications.

## Instructor Notes on Framing

This module should not be framed as "machine learning solves band gaps." A better framing is: "machine learning can identify statistical patterns in composition-property data, and those patterns are scientifically useful when interpreted with chemical judgment." The strongest learning moments often come from the errors.
