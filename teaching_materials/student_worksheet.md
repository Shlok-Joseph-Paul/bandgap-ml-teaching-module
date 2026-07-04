# Student Worksheet: Predicting Experimental Band Gaps from Chemical Formula

In this activity, you will use `pymatgen`, `matminer`, and `scikit-learn` to predict experimental semiconductor band gaps from chemical formula. The goal is to understand both what a composition-based machine-learning model can learn and what it cannot know from formula alone.

## How the Notebook Works

The notebook follows this workflow:

```text
chemical formula -> pymatgen Composition -> matminer features -> machine-learning model -> predicted band gap -> chemical interpretation
```

1. What role does `pymatgen` play in the workflow?
2. What role does `matminer` play in the workflow?
3. What role does `scikit-learn` play in the workflow?
4. Why do we need both numerical evaluation and chemical interpretation?

## 1. Pre-Lab Chemistry Predictions

Before running the notebook, use your chemistry intuition to predict qualitative band gap trends.

1. Which material classes do you expect to have relatively large band gaps? Consider oxides, sulfides, halides, elemental semiconductors, lead chalcogenides, and III-V semiconductors.
2. Which material classes do you expect to have relatively small band gaps?
3. Choose two classes from the list above and justify your predictions using periodic trends, bonding, electronegativity, and atomic size.
4. Where would you place Si, GaAs, CdTe, PbS, TiO2, and CsPbBr3 on a rough small-to-large band gap scale?

## 2. Understanding the Dataset

The notebook loads a public experimental band gap dataset from `matminer`.

1. What is the input variable used by the model?
2. What is the target, or output variable, the model is trying to predict?
3. What are the units of the target variable?
4. Why might experimental band gaps vary between different literature sources or databases?
5. Why is this activity an example of supervised learning?

## 3. Formula Parsing with pymatgen

`pymatgen` converts formulas into `Composition` objects that Python can inspect.

1. What information is contained in a chemical formula?
2. What information is missing from a chemical formula?
3. For each example, list the elements and their relative amounts:
   1. Si
   2. GaAs
   3. CdTe
   4. PbS
   5. TiO2
   6. CsPbBr3
4. Why might two materials with the same formula have different band gaps?
5. Why is a formula such as `CsPbBr3` not enough information to fully describe a real sample?

## 4. Featurization with matminer

Machine-learning models need numbers as inputs. `matminer` creates numerical descriptors, called features, from each composition.

1. In your own words, what is a feature?
2. Why can a model not directly learn from formula strings such as `TiO2` or `GaAs`?
3. Identify at least five chemically meaningful feature types that could help predict band gaps. Consider electronegativity, atomic number, atomic radius, group number, and valence electron count.
4. Choose one feature type and explain why it might be related to electronic structure or bonding.
5. Why can feature names from automated featurizers look long or technical?

## 5. Model Training and Evaluation

The notebook trains a `DummyRegressor` baseline and a `RandomForestRegressor`.

1. What does the baseline model predict for every material?
2. Report the MAE and R2 for the baseline model.
3. Report the MAE and R2 for the random forest model.
4. Which model performs better? What evidence supports your answer?
5. What does MAE mean in units of eV?
6. What does it mean if R2 is near 0 or negative?
7. Why is it useful to compare a flexible model against a simple baseline?

## 6. Interpreting the Parity Plot

The parity plot compares predicted band gaps with experimental band gaps.

1. What would perfect prediction look like on this plot?
2. In what band gap range does the model appear to perform well?
3. In what band gap range does the model appear to perform poorly?
4. Does the model tend to overpredict, underpredict, or show different behavior in different regions?

## 7. Interpreting Feature Importance

The random forest reports which features were most useful for making predictions.

1. List the top five most important features from the notebook.
2. Do these features make chemical sense? Explain one example.
3. Why should feature importance not automatically be interpreted as causation?
4. What other evidence would you want before making a chemical claim based on feature importance?
5. How is permutation importance different from built-in tree feature importance?

## 8. Analyzing Model Failures

Large errors can reveal the limits of a composition-only model.

1. Examine the largest overpredictions. Which formulas appear, and how large are the errors?
2. Examine the largest underpredictions. Which formulas appear, and how large are the errors?
3. What information might the model be missing for these cases?
4. In your answer, consider crystal structure, polymorphs, defects, stoichiometry, synthesis history, and measurement uncertainty.

## Optional Extension: Improving the Model and Studying Edge Cases

The optional notebook extension asks whether a more flexible model helps and whether model errors are concentrated in certain chemical families.

1. In the edge-case clinic, are the largest errors mostly high-gap or low-gap materials?
2. Are the largest errors mostly overpredictions or underpredictions? Use the signed error column in your answer.
3. Which simple chemical family has the largest mean absolute error? Which has the smallest?
4. Does the `HistGradientBoostingRegressor` improve MAE compared with the random forest?
5. Does the model improvement appear to help all chemical families equally?
6. Compare the built-in random forest feature importances with the permutation importances. Which features appear important in both lists?
7. Why should feature importance not automatically be interpreted as causation?
8. Which missing information would likely help the most for the difficult edge cases: structure, processing, defects, dimensionality, or measurement details?
9. Why might composition-only prediction be especially limited for quantum dots and nanocrystals?

## 9. Reflection Questions

Use these questions to connect the machine-learning workflow back to materials chemistry.

1. What did the model learn from chemical composition?
2. Why is composition alone insufficient for predicting real materials properties?
3. How would this problem change for quantum dots or nanocrystals?
4. What additional data would improve the model?
5. What is one way machine learning can help materials discovery?
6. What is one way machine learning can mislead us?
7. Which glossary term from the notebook was most important for your understanding, and why?
