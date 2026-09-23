# OPIM 5512 - Lab 2: Explaining a Model (SHAP)

**Module 2 - Tuning Models & Explainable AI.** Tonight is half lecture (what SHAP is) and half hands-on
**with GitHub** - the same branch -> pull request -> review -> merge workflow you used in Lab 1.

**The deliverable is a repo, not a notebook.** Two partners explain the *same* model two ways, then merge.

- **Partner A - global** -> `notebooks/Lab2_A_Global_SHAP.ipynb`, branch `dev-global`
- **Partner B - local**  -> `notebooks/Lab2_B_Local_SHAP.ipynb`,  branch `dev-local`

## SHAP in five sentences (the lecture, in short)

1. A good model is not the finish line - you have to be able to say **how it decided**.
2. **SHAP** gives every feature, for every prediction, a number: how many **MW** it pushed the
   prediction **up (+)** or **down (-)** from the average prediction.
3. Add a row's SHAP values to the average and you get that exact prediction - it's **additive and honest**.
4. **Global** = stack all rows to see which features matter overall, and in which direction (beeswarm).
5. **Local** = one row, one prediction, one story (waterfall) - the answer you give a stakeholder.

## What's already here (you build none of it)

```
.
|-- README.md                 <- this file (data dictionary below)
|-- REPORT.md                 <- fill the arrow lines at the end; image links already match
|-- data/energy_model_data.csv    <- the Lab 1 joined data, one row per hour
|-- images/                   <- your PNGs go here
`-- notebooks/
    |-- Lab2_A_Global_SHAP.ipynb   (A)
    |-- Lab2_B_Local_SHAP.ipynb    (B)
    `-- Lab2_Joint_Optional.ipynb
```

## What you add tonight

| who | makes | how it gets to the repo |
|---|---|---|
| A | `images/importances_builtin.png` (given) + `images/shap_global.png` (your beeswarm) | download -> drag into `images/` |
| A | the notebook with your one SHAP line | Colab **File -> Save** to `dev-global` |
| B | `images/predicted_vs_actual.png` (given) + `images/shap_local.png` (your waterfall) | download -> drag into `images/` |
| B | the notebook with your one SHAP line | Colab **File -> Save** to `dev-local` |
| both | `REPORT.md` - one sentence per plot | edit on `main` after both PRs merge |

## Data dictionary - `data/energy_model_data.csv` (743 rows, one per hour)

| column | meaning | units |
|---|---|---|
| `hour` | timestamp, the hour it begins | - |
| `temp_f` | air temperature | deg F |
| `hour_of_day` | 0-23 | hour |
| `dewpoint_f` | dew point | deg F |
| `humidity_pct` | relative humidity | % |
| `wind_kt` | wind speed | knots |
| `weekend` | 1 = Sat/Sun | 0/1 |
| `load_mw` | New England demand (**what the model predicts**) | MW |

## Model's Built-in Feature Importances
`hour_of_day` is by far the dominant feature in the model's built-in ranking, with `dewpoint_f` and `temp_f` a distant second and third, and `weekend`, `humidity_pct`, and `wind_mph` contributing comparatively little.

## SHAP Beeswarm (Global — required plot)
`hour_of_day` is the dominant driver of predicted demand, with SHAP values increasing steadily as the hour value rises (red, high hours, on the positive side; blue, low hours, on the negative side), showing demand builds through the day rather than spiking narrowly. `dewpoint_f` and `temp_f` are secondary drivers, while `weekend`, `humidity_pct`, and `wind_kt` contribute comparatively little.

## Boxplot of SHAP Values per Feature
The boxplot shows `hour_of_day` has by far the widest spread of SHAP values, meaning its effect on individual predictions varies more than any other feature, while the remaining features cluster tightly near zero impact.

## Violin Plot of SHAP Values
This retells the beeswarm's story as a density shape, confirming the same `hour_of_day` dominance and wide swing, with the smaller features showing narrow, low-impact distributions.

## Dependence Plot (temp_f)
As `temp_f` increases, its SHAP value trends upward too, suggesting warmer temperatures generally push predicted demand higher, with the color coding likely reflecting an interaction with a second feature.

## Absolute Sum of SHAP Values per Feature
This ranks features by total absolute impact across all predictions, and it lines up with the earlier plots: `hour_of_day` first, `dewpoint_f` and `temp_f` next, with the rest trailing well behind.
