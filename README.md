# SWIFT–BayesFlow Implementation for Reading Behavior Modeling

This repository contains the implementation of a simplified **SWIFT (Saccade Generation With Inhibition by Foveal Targets)** model combined with **BayesFlow**, an amortized simulation-based inference framework.  
The project was developed as part of the **Statistical Bayesian Inference (SBI)** course at **TU Dortmund University**.  

**Authors:**  
- Furkan Duman  
- Ulaş Naki Turan  

---

## 📖 Introduction

Reading is a complex cognitive skill involving the dynamic coordination of visual and linguistic processes. Eye movements during reading, such as fixations and saccades, are not random but reflect our moment-to-moment processing of text. To capture the underlying cognitive dynamics, researchers use process-oriented models that link hidden mental states to measurable eye-tracking data.

One influential framework is the **SWIFT model** [Engbert et al., 2002], a dynamical model of saccade generation. However, its computational complexity makes parameter estimation challenging in large-scale applications.  

To address this, we build upon a **simplified SWIFT model** [Engbert & Rabe, 2024], retaining core principles while reducing computational demands. Our focus lies on three key parameters:

- **ν (nu):** shape parameter of the processing span  
- **r:** overall processing rate  
- **μ_T:** mean saccade timer interval  

In addition, the saliency noise parameter **η** is fixed at `10⁻³` to ensure stochasticity in gaze trajectories.  

For inference, we employ **BayesFlow** [Radev et al., 2020], which enables *amortized simulation-based inference* (SBI). Once trained, BayesFlow provides instantaneous Bayesian posterior estimation, bypassing costly grid search or MCMC sampling.  

This SWIFT–BayesFlow pipeline provides a **scalable tool for cognitive modeling**, allowing real-time recovery of reading parameters from noisy eye-tracking data.

---

## 📂 Repository Structure

- `main.ipynb` → Jupyter Notebook containing the full implementation and experiments  
- `requirements.txt` → Dependencies needed to run the notebook  
- `README.md` → Project documentation (this file)  

---

## ⚙️ Installation

Install dependencies:

```bash
pip install -r requirements.txt


🚀 How to Run

Run the Jupyter Notebook:

jupyter notebook main.ipynb


Training progress and diagnostics will be displayed inside the notebook, and figures will be generated inline.

📊 Features

Data Preprocessing: Reads and filters fixation data.

Simulator: Generates synthetic scanpaths using the simplified SWIFT model.

BayesFlow Integration: Provides amortized inference for estimating parameters (ν, r, μ_T).

Training & Diagnostics: Online training with diagnostics such as posterior plots and pairwise distributions.

Real Participant Inference: Demonstrates parameter recovery from real eye-tracking data.

🔬 Results

The workflow is capable of recovering posterior distributions for ν, r, and μ_T.

Diagnostics include posterior histograms, scatter plots, and pairwise comparisons.

Real participant data yields interpretable estimates of reading-related cognitive parameters.



📌 References

Engbert, R., Longtin, A., & Kliegl, R. (2002). A dynamical model of saccade generation in reading based on spatially distributed lexical processing. Vision Research, 42(5), 621–636.

Engbert, R., & Rabe, M. M. (2024). Tutorial on dynamical modeling of eye movements in reading. OSF Preprint.

Radev, S. T., et al. (2020). BayesFlow: Learning complex stochastic models with invertible neural networks. arXiv preprint arXiv:2003.06281.

🙌 Acknowledgments

This project was carried out as part of the SBI course at TU Dortmund University.
We thank our instructors for guidance and valuable discussions.
