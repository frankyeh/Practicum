## 🧭 Workshop Week 4 Outline

1. **Differential Tractography**  
   - Cross-sectional analysis  
   - Longitudinal analysis  

2. **Correlational Tractography**  
   - Cross-sectional analysis / group comparison  
   - Longitudinal analysis  

---

## 🧠 Session 1: Differential Tractography

Adds an additional **termination criterion**:  
→ **Tracking stops when the signal difference exceeds a defined threshold**

📂 **Example Dataset:**  
- SCA2 study: QSDR `.fz` files

---

### 🧪 Hands-On Exercises

#### 🔧 Create a Population-Average Template

#### 📊 Cross-Sectional Analysis
- Build a population average template  
- Compare **patient vs. average** and **control vs. average**  
- Compute **false discovery rate**:  
  *(Findings in controls) / (Findings in patients)*

#### 🧬 Longitudinal Analysis
- Compare **follow-up vs. baseline** for patients and controls  
- Compute **false discovery rate** similarly  

---

## 🧠 Session 2: Correlational Tractography

Identifies fiber tracts that **correlate with a variable or condition**  
→ Based on **Spearman correlation** across subjects

<img src="https://github.com/user-attachments/assets/fc4d71e9-09c3-471a-8b91-509607e31f1e" width="400"/>

---

### 📂 Prepare the Database

Aggregate metrics (e.g., FA, QA) from:
1. QSDR reconstructed files (`*.qsdr.fz`)  
2. MNI-space NIfTI files (`*.nii.gz`)  

📌 **Example Dataset:** SCA2 study

---

### 🧪 Analysis Types

<img src="https://user-images.githubusercontent.com/275569/197086945-5eb4bbc9-8a01-4bc6-a59d-84bcbe1f3735.png" width=600/>

#### 📊 Cross-Sectional Analysis  
- Correlate diffusion metrics with variables across subjects
- Post-tracking analysis

#### 🧬 Longitudinal Analysis  

- Changes in patients
- Changes in healthy control
- Changes correlated with disease using filtered changes

