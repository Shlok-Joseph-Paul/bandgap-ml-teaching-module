# Assessment Rubric

This rubric is designed for the full notebook plus worksheet activity. Adjust point values for a shorter in-class version.

## 100-Point Rubric

| Category | Points | Strong performance |
|---|---:|---|
| Pre-lab chemistry predictions | 10 | Makes reasonable qualitative band gap predictions and justifies them with periodic trends, bonding, electronegativity, and atomic size. |
| Dataset and workflow understanding | 10 | Correctly identifies input, target, units, supervised-learning framing, and reasons experimental values may vary. |
| Formula parsing and missing information | 10 | Correctly explains what `pymatgen` compositions contain and clearly identifies missing structure, defects, phase, morphology, and measurement details. |
| Magpie descriptor interpretation | 15 | Explains features as numerical descriptors, interprets statistic-property names, and connects at least three descriptors to chemical intuition without overclaiming causation. |
| Model training and metrics | 15 | Correctly reports baseline and model MAE/R2, explains MAE in eV, and uses the baseline comparison appropriately. |
| Plot and feature-importance interpretation | 15 | Interprets the parity plot, built-in importance, and permutation importance with appropriate caution about correlation and causation. |
| Error and edge-case analysis | 15 | Uses absolute and signed errors to discuss model failures and connects difficult cases to missing chemical, structural, or experimental information. |
| Reflection and scientific judgment | 10 | Gives thoughtful answers about composition-only limitations, quantum dots or nanocrystals, useful additional data, and responsible use of machine learning. |

## Optional Interactive Challenge Add-On

Use this section if students complete the chemistry-guided modeling challenge.

| Category | Points | Strong performance |
|---|---:|---|
| Hypothesis before modeling | 5 | States a clear chemistry-based hypothesis before running experiments. |
| Experiment records | 10 | Records at least three experiments with feature strategy, model choice, overall metrics, family metrics, and a concise note on what changed. |
| Chemistry-guided interpretation | 10 | Explains why selected feature groups should matter and compares chemistry-guided choices with automatic feature selection. |
| Balanced conclusion | 5 | Distinguishes predictive improvement from physical understanding and identifies remaining difficult materials. |

The add-on can be graded as 30 extra points or scaled into the 100-point rubric by replacing part of the reflection and edge-case categories.

## Suggested Letter-Grade Bands

- A range: 90 to 100. Accurate, complete, chemically thoughtful, and appropriately cautious.
- B range: 80 to 89. Mostly correct with minor gaps in interpretation or supporting detail.
- C range: 70 to 79. Basic workflow is understood, but chemical reasoning or model interpretation is thin.
- D range: 60 to 69. Major misconceptions about features, metrics, or composition-only limitations.
- Needs revision: below 60. Incomplete work or answers that treat model output as unquestioned truth.

## Common Feedback Comments

- "Good model comparison, but explain what MAE means in eV."
- "This feature is chemically relevant, but importance does not prove causation."
- "You identified a large error; now connect it to missing structure, defects, or measurement details."
- "Your feature choice improved MAE, but check whether it helped all chemical families equally."
- "Your quantum dot answer should mention size, surface chemistry, dielectric environment, and confinement."

## Minimal In-Class Grading Option

For a 75-minute class, grade only:

- one pre-lab prediction,
- one descriptor explanation,
- baseline versus random forest metrics,
- one parity-plot observation,
- one large-error explanation,
- one final reflection on composition-only limitations.

This keeps the grading lightweight while preserving the main learning goals.
