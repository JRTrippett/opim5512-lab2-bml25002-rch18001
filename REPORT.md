# Lab 2 report - explaining our demand model

**Authors:** _replace this line with your name_
<!-- ^ You and your partner BOTH edit THIS ONE LINE with your name, each on your own branch.
     When the second pull request merges you'll get a merge conflict right here - that's on
     purpose. Resolve it by keeping BOTH names. Everything else below is in separate sections,
     so those merge cleanly. -->

*Two people, one model, two kinds of explanation. Fill in YOUR section; leave your partner's alone.
Replace every `=>` with a real sentence; every number gets a unit.*

## Global - what the model leans on overall (Partner A)
![built-in importances](images/importances_builtin.png)

=> One sentence: which feature does the model lean on most, by magnitude alone?

![SHAP beeswarm](images/shap_global.png)

=> One sentence: which feature is #1, and does a HIGH value push demand up or down?

## Local - one hour explained (Partner B)
![predicted vs actual](images/predicted_vs_actual.png)

=> One sentence: does it track the diagonal? roughly how far off is a typical hour?

![SHAP waterfall for the peak hour](images/shap_local.png)

=> One sentence: for the peak hour, what pushed the prediction up, and what pulled it down?

## Combined (both, optional)
![SHAP dependence](images/shap_dependence.png)

=> One sentence tying Lab 1 to Lab 2: *"it's the clock as much as the thermometer"* - in your words.

## What this explanation can't tell us
=> One honest sentence. (SHAP explains THIS model, not the real world; one summer, one region; correlation, not proof.)
