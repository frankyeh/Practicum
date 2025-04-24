## 🧭 Workshop Week 4 Outline

1. **Differential Tractography**  
   - Cross-sectional analysis  
   - Longitudinal analysis  

2. **Correlational Tractography**  
   - Cross-sectional analysis / group comparison  
   - Longitudinal analysis  

---

## 🧠 Session 1: Differential Tractography

<img src="https://github.com/user-attachments/assets/c298a7f5-e8cc-4224-a1f5-d04a180233a7" width=800/>

Adds an additional **termination criterion**:  
→ **Tracking stops when the signal difference exceeds a defined threshold**

### 🧪 Hands-On Exercises

📂 **Example Dataset:**  
- [OpenNeuro (disease)][ds001378] SCA2 study

#### 🧬 Longitudinal Analysis
- Compare **follow-up vs. baseline** for patients
- Compare **follow-up vs. baseline** for controls  
- Compute **false discovery rate**:  
  *(Findings in controls) / (Findings in patients)*

#### 📊 Cross-Sectional Analysis

- Build a population average template
  - Download control subject's qsdr.fz file: select matching → `*control*ses-01*qsdr.fz`
  - [Tractography (Batch)] → [Create Population Average]
- Compare **patient vs. average** and **control vs. average**  
- Compute **false discovery rate**:  
  *(Findings in controls) / (Findings in patients)*

---

## 🧠 Session 2: Correlational Tractography

<img src="https://user-images.githubusercontent.com/275569/197086945-5eb4bbc9-8a01-4bc6-a59d-84bcbe1f3735.png" width=600/>

Identifies fiber tracts that **correlate with a variable or condition**  
→ Based on **Spearman correlation** across subjects

---

### 📂 Prepare the Database

Aggregate metrics (e.g., FA, QA) from: QSDR reconstructed files (`*.qsdr.fz`)  

📌 **Example Dataset:** SCA2 study

---

<img src="https://github.com/user-attachments/assets/fc4d71e9-09c3-471a-8b91-509607e31f1e" width="400"/>

### 🧪 Analysis Types

#### 📊 Cross-Sectional Analysis  
- Correlate diffusion metrics with variables across subjects
- Post-tracking analysis

#### 🧬 Longitudinal Analysis  

- Changes in patients
- Changes in healthy control
- Changes correlated with disease using filtered changes

#### 🧬 Post-hoc Analysis  
- Segment tracts and compute associated values
