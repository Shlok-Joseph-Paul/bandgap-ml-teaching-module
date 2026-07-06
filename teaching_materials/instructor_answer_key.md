# Instructor Answer Key: Sample Responses

This guide provides sample responses and teaching notes for the student worksheet. It is not meant to prescribe one exact answer. Strong student responses should combine correct machine-learning vocabulary with chemically reasonable interpretation.

Numerical results may vary with package versions, dataset availability, random seed, and whether students use the full dataset or a smaller sample.

## How the Notebook Works

1. `pymatgen` parses formula strings into `Composition` objects that store elements and stoichiometric ratios.
2. `matminer` converts compositions into numerical descriptors, such as Magpie elemental-property statistics.
3. `scikit-learn` splits data, trains regression models, makes predictions, and calculates metrics.
4. Numerical evaluation shows whether a model predicts well. Chemical interpretation asks whether the patterns and failures make scientific sense.

## 1. Pre-Lab Chemistry Predictions

Students may rank classes differently, but reasonable expectations include:

- Larger gaps: many oxides and halides, especially highly ionic compounds with light elements.
- Intermediate gaps: many III-V semiconductors and elemental semiconductors such as Si.
- Smaller gaps: many lead chalcogenides and heavy chalcogenides because heavier atoms, larger radii, polarizability, and spin-orbit effects often reduce gaps.

Good justifications should mention electronegativity differences, orbital overlap, atomic size, periodic trends, ionicity, covalency, and the fact that composition alone is not enough.

## 2. Understanding the Dataset

1. Input variable: chemical composition or formula.
2. Target variable: experimental band gap.
3. Units: electronvolts, eV.
4. Experimental band gaps may vary because of polymorphs, temperature, defects, off-stoichiometry, grain size, measurement method, sample preparation, and literature reporting differences.
5. It is supervised learning because each input composition is paired with a known target value.

## 3. Formula Parsing with pymatgen

Chemical formulas contain element identities and stoichiometric ratios. They do not contain crystal structure, phase, polymorph, site disorder, defects, sample morphology, synthesis history, or measurement conditions.

Example parsing:

| Formula | Elements and relative amounts |
|---|---|
| `Si` | Si: 1 |
| `GaAs` | Ga: 1, As: 1 |
| `CdTe` | Cd: 1, Te: 1 |
| `PbS` | Pb: 1, S: 1 |
| `TiO2` | Ti: 1, O: 2 |
| `CsPbBr3` | Cs: 1, Pb: 1, Br: 3 |

Strong answers should explain that two materials with the same formula can have different structures, defect concentrations, phases, or particle sizes, leading to different measured band gaps.

## 4. Featurization with matminer

A feature is a numerical descriptor used as a model input. Examples include mean electronegativity, range of atomic number, mean covalent radius, periodic-table row or column, and valence-electron counts.

Models cannot use formulas such as `TiO2` directly because most standard regression algorithms operate on numerical arrays. Featurization translates chemistry into numbers.

Good responses should also recognize that automated feature names can look technical because they combine a statistic and an elemental property, such as `MagpieData mean Electronegativity`.

## 5. Model Training and Evaluation

The `DummyRegressor` predicts a simple constant, usually the mean training-set band gap. It is a baseline.

The random forest should normally outperform the baseline. Students should support that claim with lower MAE and higher R2.

MAE is the average absolute prediction error in eV. For example, an MAE of 0.45 eV means the model is off by about 0.45 eV on average. R2 near 1 is better; R2 near 0 means the model is similar to predicting the mean; negative R2 means worse than that baseline.

## 6. Interpreting the Parity Plot

Perfect prediction would put every point on the diagonal line where predicted band gap equals actual band gap.

Students should identify regions where points cluster near the diagonal and regions with large vertical deviations. Common observations may include more scatter for high-gap materials or underrepresented chemistries, but the exact pattern can vary.

Overprediction means the point is above the parity line. Underprediction means the point is below the parity line.

## 7. Interpreting Feature Importance

Feature importance lists may vary. Strong answers should:

- list the top features from the notebook output,
- explain at least one feature chemically,
- avoid claiming that feature importance proves causation, and
- mention correlated features, model bias, hidden variables, and missing structure as reasons for caution.

Permutation importance is usually a more direct test of predictive reliance: it measures how much model performance drops when one feature is shuffled. It is still model- and dataset-dependent.

## 8. Analyzing Model Failures

Good answers should distinguish overpredictions from underpredictions using signed error and should discuss why large errors can be scientifically informative.

Likely missing information includes:

- crystal structure and coordination environment,
- polymorph or phase,
- defects and non-stoichiometry,
- synthesis and processing history,
- temperature and measurement method,
- particle size and dimensionality, especially for nanocrystals or quantum dots,
- dataset noise or inconsistent literature values.

## Optional Extension

For the edge-case clinic, accept answers that use the notebook output directly. Students should identify whether large errors cluster in high-gap or low-gap materials and whether signed errors are mostly positive or negative.

For the chemical-family analysis, strong students will avoid overgeneralizing from a small family sample. A family with high MAE may be genuinely difficult, underrepresented, chemically diverse, or affected by missing structure and measurement details.

For the model comparison, students should report the MAE and R2 values from their run. If gradient boosting improves MAE, they should still ask whether it improved all families equally. If it does not improve, they should discuss train/test split, hyperparameters, dataset size, and whether composition-only features are the limiting factor.

## Interactive Challenge

Strong responses should state a hypothesis before running experiments. For example:

```text
I expect electronegativity and valence-electron features to matter because band gaps depend on bonding polarity and band filling.
```

Good experiment records should include:

- feature strategy,
- selected feature groups or automatic `k`,
- model type,
- overall MAE and R2,
- target chemical family,
- family-specific MAE,
- a brief explanation of what changed.

Credit chemistry-guided reasoning even when it does not improve MAE. A scientifically useful model is not always the most accurate model, and a very accurate model is not automatically physically interpretable.

## Reflection Questions

Strong final reflections should include these ideas:

- The model learned statistical relationships between composition-derived features and experimental band gaps.
- Composition alone is incomplete because real materials properties depend on structure, defects, processing, morphology, and measurement conditions.
- Quantum dots and nanocrystals require additional descriptors for size, shape, surface ligands, dielectric environment, and quantum confinement.
- Additional useful data would include crystal structures, polymorph labels, temperature, synthesis details, defect chemistry, measurement method, and uncertainty.
- Machine learning can help screen materials, identify trends, and prioritize experiments.
- Machine learning can mislead if users overinterpret correlations, ignore data quality, extrapolate outside the training domain, or treat predictions as mechanistic proof.
