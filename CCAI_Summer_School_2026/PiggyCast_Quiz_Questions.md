# PiggyCast Tutorial — Quiz Questions
## CCAI Virtual Summer School 2026

---

### Question 1 (Multiple Choice)
**What does Geopotential Height at 500 hPa (Z500) represent, and why is it used to evaluate weather forecasting models?**

A) The height of the ocean surface at 500 km offshore; it is used because oceans drive weather systems.

B) The altitude above sea level where atmospheric pressure equals 500 millibars; it captures large-scale atmospheric circulation patterns that steer surface weather systems.

C) The temperature of the atmosphere at 500 km altitude; it is used because temperature is the most measurable weather variable.

D) The cumulative rainfall over 500 hours; it is used because precipitation is the most climate-relevant variable.

**✅ Correct answer: B**

*Explanation:* Z500 sits roughly at mid-troposphere (~5.5 km altitude). Its large-scale patterns (ridges and troughs) steer storms, droughts, and heatwaves, making it a standard benchmark variable in weather forecasting evaluation frameworks like WeatherBench 2.

---

### Question 2 (Multiple Choice)
**PiggyCast is a stacking ensemble model. Which of the following best describes what "stacking" means in this context?**

A) Stacking multiple copies of the same model to reduce variance.

B) Running NWP models sequentially so each one corrects the errors of the previous one.

C) Training a new meta-model (XGBoost) on the outputs of several base models (GraphCast, Pangu, NeuralGCM, IFS HRES) to produce a combined, more accurate forecast.

D) Averaging the outputs of base models with equal weights to produce a consensus forecast.

**✅ Correct answer: C**

*Explanation:* Stacking (also called "stacked generalisation") trains a meta-learner on the predictions of base models rather than simply averaging them. This allows the meta-model to learn the relative strengths and weaknesses of each base model, rather than treating them equally.

---

### Question 3 (True / False)
**True or False: At short lead times (24-96 hours), PiggyCast always outperforms all base models, while at long lead times (120-240 hours) the base models catch up.**

**✅ Correct answer: False**

*Explanation:* The opposite pattern is observed. At 48 hours, NeuralGCM outperforms PiggyCast (RMSE ~60.8 m^2/s^2 vs ~64.2 m^2/s^2). PiggyCast's advantage grows with lead time, and it outperforms all base models at longer horizons (≥ 120–144 hours). This is because individual model biases compound over time, while the stacking ensemble learns to cancel out those biases.

---

### Question 4 (Multiple Choice)
**A researcher wants to deploy PiggyCast operationally to generate real-time 10-day weather forecasts for a national meteorological service. Which of the following is the MOST important limitation they must address first?**

A) The XGBoost model uses too many trees and should be simplified.

B) PiggyCast produces deterministic forecasts without uncertainty quantification, making it unsuitable for risk-based decision-making without further development.

C) ERA5 data is too spatially coarse and should be replaced with satellite images.

D) PiggyCast cannot be run on a standard laptop and requires a supercomputer.

**✅ Correct answer: B**

*Explanation:* Operational weather forecasting for emergency management, agriculture, and energy dispatch requires probabilistic output (e.g., probability of exceeding a threshold) so that decision-makers can weigh risks. A deterministic forecast alone does not communicate confidence or uncertainty. Other listed issues are either not primary concerns (XGBoost complexity, laptop capability) or secondary to the uncertainty issue.

---

*Note to CCAI team: Questions 1–4 cover the forecasting task (Q1), ensemble methodology (Q2), temporal performance interpretation (Q3), and responsible/deployment considerations (Q4). These map to Learning Objectives 1, 2, 4, and 5 respectively.*
