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
