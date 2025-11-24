Perfect — here’s a clean plan for your **LaTeX PDF report** and your **README.md** so your project looks professional, scientific, and portfolio-ready.
This mirrors the uploaded paper’s structure while ensuring your version is modern and unique.

---

# ✅ **1. Recommended LaTeX Structure (matches the uploaded paper)**

Below is the **exact outline** you should use in your LaTeX PDF.
I can generate the full `.tex` file for you if you want.

---

# 📄 **LaTeX Report Structure**

## **Title Page**

* Title: *Kepler Mission: Exoplanet Classification Using Machine Learning*
* Your name
* Date
* Course/project (optional)

---

## **Abstract**

A short summary of:

* Using Kepler KOI dataset
* Goal: classify as Confirmed / Candidate / False Positive
* ML models used
* Best model’s accuracy
* One-sentence conclusion

---

## **1. Introduction**

Explain:

* What the Kepler mission is
* How transit detection works
* What KOIs are
* Why classification is important
* What you'll do in the report (replicating the structure of the reference paper)

---

## **2. Related Work**

Summaries of:

* Random Forest classification of transit candidates
* Deep learning for Kepler-90 / Kepler-80
* Why ML is useful

---

## **3. Dataset Overview**

You describe:

* KOI dataset
* Explanation of variables
* Three classes (confirmed, candidate, false positive)
* Total rows after cleaning
* Important features (period, duration, depth, star parameters)

Include a small table, e.g.:

| Feature    | Description         |
| ---------- | ------------------- |
| koi_period | Orbital period      |
| koi_depth  | Transit depth       |
| koi_prad   | Planet radius       |
| koi_steff  | Stellar temperature |
| koi_score  | Confidence score    |

---

## **4. Preprocessing**

State everything you did:

* Dropped irrelevant columns (names, IDs)
* Imputed missing values
* Feature selection (your chosen features)
* Scaled numeric features
* Oversampling with SMOTE
* Train/test split

Add a table of class imbalance before/after SMOTE.

---

## **5. Modeling**

Describe each model:

### **5.1 Logistic Regression**

Baseline performance.

### **5.2 Decision Tree**

Interpretability + feature importance.

### **5.3 Random Forest**

Likely best model.

### **5.4 Neural Network**

1 hidden layer.

### **5.5 Training Setup**

* Cross-validation
* Hyperparameters

---

## **6. Results**

Include:

* Confusion matrices
* Precision, recall, F1
* Accuracy
* Table comparing models:

| Model | Accuracy | Precision | Recall | F1 |
| ----- | -------- | --------- | ------ | -- |

Add plots:

* Feature importance
* ROC curve (optional)

---

## **7. Discussion**

Interpret the results:

* Why RF is best (non-linear features, noise tolerance)
* Why logistic regression underperforms
* Neural network sensitivity

---

## **8. Conclusion**

Summarize:

* Best model
* Accuracy achieved
* Implications

---

## **9. Future Work**

Ideas:

* Deep CNNs
* Light curve time-series modeling
* Incorporating Gaia DR3 data
* Improving oversampling methods

---

## **References**

Use the ones from the PDF:

* NASA Exoplanet Archive
* McCauliff et al.
* Shallue & Vanderburg
* Kaggle repository



Got you — let’s break this down **cleanly and clearly** so you understand *exactly* why these columns matter and why they’re ideal for exoplanet classification.

These features are **the standard “core” ML features used in exoplanet vetting**, including by NASA pipelines.
They represent **transit geometry**, **signal quality**, and **stellar properties**, which together determine whether a signal is likely to be a real planet.

---

# ⭐ **Here are the columns and what each represents (simple + why it matters for ML):**

I'll explain each in two lines:

* **What is it?**
* **Why it's useful for predicting planet vs false positive**

---

# 🌍 **1. `koi_score` — Disposition score**

**What:** NASA's confidence score (0–1) from manual vetting.
**Why:** Higher score = more likely to be a real planet. Strong predictive feature.

---

# ⚠️ **False Positive Flags**

These four are extremely important — they directly encode *why* a candidate might not be a planet.

---

### **2. `koi_fpflag_nt` — Not Transit-like**

**What:** Flag if the signal doesn’t resemble a transit curve.
**Why:** If 1 → very likely a false positive.

### **3. `koi_fpflag_ss` — Stellar eclipse**

**What:** Indicates eclipsing binary behavior.
**Why:** Massive signal depth → likely a binary star, not a planet.

### **4. `koi_fpflag_co` — Centroid Offset**

**What:** Detects shifts in star position during transit.
**Why:** A shift means the dimming comes from a nearby star → false alarm.

### **5. `koi_fpflag_ec` — Ephemeris Match**

**What:** Signal matches the period of another known binary.
**Why:** Strong indicator of contamination, not a planet.

---

# 🕒 **Transit Geometry**

These are the “shape” of the transit. Real planets produce clean, predictable shapes.

---

### **6. `koi_period` — Orbital period (days)**

**What:** How long the planet takes to orbit.
**Why:** Unrealistically short or long periods can indicate noise or stellar activity.

---

### **7. `koi_time0bk` — Transit epoch (BKJD)**

**What:** Reference time when transit occurs.
**Why:** Helps characterize periodicity consistency → real planets are very regular.

---

### **8. `koi_impact` — Impact parameter**

**What:** How central the transit path is (0 = center, 1 = edge).
**Why:** Very high values → grazing events → more often false positives.

---

### **9. `koi_duration` — Transit duration (hrs)**

**What:** How long the transit lasts.
**Why:** Duration must match expected orbital period and star size.

---

### **10. `koi_depth` — Transit depth (ppm)**

**What:** Amount of dimming.
**Why:** One of the strongest features:

* Deep = binary star
* Moderate = planet
* Very small = noise

---

# 🪐 **Planetary parameters**

### **11. `koi_prad` — Planet radius (Earth radii)**

**What:** Estimated radius.
**Why:** Extremely large radius → not a planet → likely eclipsing binary.

---

### **12. `koi_teq` — Equilibrium temperature (K)**

**What:** Estimated temperature of the planet.
**Why:** Helps identify if the transit makes physical sense.

---

### **13. `koi_insol` — Insolation flux**

**What:** Energy received from star compared to Earth.
**Why:** Extreme values sometimes indicate stellar artifacts.

---

# 📡 **Signal Quality Features (VERY IMPORTANT)**

### **14. `koi_model_snr` — Signal-to-noise ratio**

**What:** Strength of the transit signal.
**Why:** One of the top predictors.

* Low SNR = junk
* High SNR = strong planet candidate

---

# ⭐ **Stellar properties**

Planet likelihood depends heavily on the star itself.

---

### **15. `koi_steff` — Stellar effective temperature (K)**

Cool vs hot stars affect detectability & planet types.

---

### **16. `koi_slogg` — Stellar surface gravity**

Distinguishes dwarfs vs giants.
Giants rarely host detectable planets via transits.

---

### **17. `koi_srad` — Stellar radius (solar radii)**

Bigger stars = shallower transits → easier to misclassify.

---

# 🗺️ **Sky location**

### **18. `ra` — Right Ascension**

### **19. `dec` — Declination**

Useful for:

* identifying star clusters (more false positives)
* cross-matching with Gaia
* background contamination likelihood

Not the strongest predictors but still helpful.

---

# 🔦 **Brightness**

### **20. `koi_kepmag` — Kepler magnitude (brightness)**

Fainter stars → noisier light curves → more false alarms.

---

# 🎯 **21. `target` — Label (0/1/2)**

This is your encoded target:

* 0 = False Positive
* 1 = Candidate
* 2 = Confirmed

---

# 📌 **Why THESE features?**

These 21 features represent the **minimal, scientifically meaningful subset** used by nearly all exoplanet ML papers.

They cover:

| Category             | Meaning                                                   |
| -------------------- | --------------------------------------------------------- |
| Transit geometry     | Does the transit look physically real?                    |
| False positive tests | Does NASA detect signs of contamination?                  |
| Planet-star relation | Does the radius/duration/depth make sense?                |
| Stellar context      | Is this the type of star where this transit is plausible? |
| Photometric SNR      | Is the signal trustworthy?                                |

This set is compact but very powerful.

Most researchers drop 200+ raw Kepler columns and keep only these — because these are the ones that actually help ML distinguish planets from false positives.

---

# 🚀 Want me to generate Notebook 02 next (feature engineering), using ONLY these useful columns?


Machine Learning Pipeline (Classification)

Load dataset

Clean and preprocess

EDA

Split into train/test

Scale numeric features

Feature selection (LASSO)

Train model on training set

Evaluate on test set using:

accuracy

precision

recall

F1

AUC

confusion matrix

Interpret results, visualize metrics

Make predictions with final model