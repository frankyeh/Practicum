# 🧪 DSI Studio Preprocessing Pipeline

<img src="https://github.com/user-attachments/assets/5102fc0a-ba86-4c61-b165-9c79498e684a" width="800"/>

**Preprocessing** in diffusion MRI involves preparing the raw data to ensure accurate analysis. It focuses on correcting technical artifacts and reducing noise, including:

- Motion and eddy current distortion correction  
- Susceptibility-induced distortion correction  

👉 In DSI Studio, these steps are integrated into the pipeline, offering a lightweight yet effective preprocessing approach.

---

## 🧭 Workshop Outline

1. **MRI Data Acquisition**
   - Best practices and recommendations for diffusion MRI scanning  
   
2. **Preprocessing DWI Data (SRC Files)**
   - Motion correction & eddy current distortion correction  
   - Susceptibility artifact correction  

3. **Diffusion Modeling: Resolving Fibers and Measuring Anisotropy**
   - Overview of DTI, GQI, and QSDR models  

---

## 🧭 Session 1: Diffusion MRI Acquisitions (15 minutes)

### ✅ Checklist 1: Sufficient Diffusion Contrast

- Use **b-value > 1,000 s/mm²** for human studies  
- ⚠️ No post-processing can recover missing diffusion contrast  

📌 *Example: HCP-YA dataset*  
b-values: **0, 1000, 2000, 3000 s/mm²**  
b-vector: **(0, 0, 1)**

<img src="https://github.com/user-attachments/assets/2a47fe2b-7a38-42d3-84c4-b69baae046bc" width="800"/>

---

### ✅ Checklist 2: Isotropic Resolution

- Ensure **slice thickness ≈ in-plane resolution**  
- If anisotropic, consider **regridding to isotropic** before analysis  

📌 *Example: OpenNeuro ds005849*  
In-plane: **1.75 mm**  
Slice thickness: **2.7 mm** → ⚠️ Not isotropic

<img src="https://github.com/user-attachments/assets/df8847c7-a585-4aa1-88e6-32e8d0e1ba70" width="800"/>

---

### ✅ Checklist 3: Reverse-Phase b0 Image

- Used to **correct susceptibility distortions**, especially in frontal and temporal lobes  
- Some tools allow T1w-based correction, but **b0 pairs are preferred**  
- **Sequence-based** corrections (e.g., readout segmentation) are also available  

📌 *Source: [FSL Topup User Guide](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/topup(2f)TopupUsersGuide.html)*

**Before Correction**  
(Phase encoding: AP, AP, PA, PA)  
<img src="https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/attachments/topup(2f)TopupUsersGuide/original_images.png" width="800"/>

**After Correction**  
<img src="https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/attachments/topup(2f)TopupUsersGuide/hifi_images.png" width="800"/>

---

### ✅ Checklist 4: Multiple b-values

**Multi-shell scheme (HCP-like)**

3 b-values: **1000 (20 directions), 2000 (40 directions), 3000 (60 directions)**

Enables robust modeling across a range of diffusion strengths

**Grid scheme (DSI-like)**

23 b-values from 0 to 4000 s/mm², distributed across 258 directions

Optimized for q-space sampling and advanced reconstruction (e.g., DSI, GQI)

---

## Session 2: Diffusion MRI Preprocessing (15 minutes)

### 🧠 Common Artifacts in Diffusion MRI Affecting the Quality, Starting from Largest

| Artifact | Cause | Consequence | Solution |
|----------|-------|-------------|----------|
| **Motion artifacts** | Subject moves during the scan | Signal dropout and inter-slice misalignment, especially along motion directions → reduced anisotropy and tracking errors | (1) Discard the scan if motion is severe<br>(2) Apply motion correction to realign images |
| **Eddy current artifacts** | Gradient-induced eddy currents distort the readout | Linear deformation within slices → spurious fibers near the brain surface, often aligned left-right in color maps | (1) Use current-canceling gradient designs (e.g., bipolar, twice-refocused)<br>(2) Apply affine image registration |
| **Susceptibility artifacts** | Magnetic field distortion near air-tissue interfaces | Signal dropout and geometric distortion along the phase-encoding direction | (1) Use sequence-based corrections (e.g., segmented EPI)<br>(2) Combine reversed-phase b0 images to correct distortion |
| **Noise** | Low signal-to-noise ratio (SNR) in DWI | Advanced models (e.g., multi-tensor) are sensitive to noise; DTI and GQI/QSDR are more robust | Apply denoising or image smoothing techniques |
| **B1 inhomogeneity** | Uneven RF coil sensitivity across the field of view | Bias in metrics sensitive to spin density (e.g., S0, QA); diffusion tensor metrics are unaffected | Apply bias field correction |
| **Gibbs ringing** | Band-limited k-space sampling | Ringing artifacts at sharp intensity transitions; usually not visible in low-SNR DWI | Use sub-voxel smoothing or total variation filtering |

Hands-on
 
  - Download [OpenNeuro ds002087](https://openneuro.org/datasets/ds002087): datasets with and without deliberate head movements for detection and imputation of dropout in diffusion MRI
  - Convert NIFTI to SRC files


---

## 🛠️ Tools for Preprocessing

**Popular Tools:**  
✅ FSL • ✅ MRtrix3 • ✅ QSIPrep • ✅ DIPY • ✅ DSI Studio

---

### 🔧 Tool Highlights

#### [FSL's topup](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/topup.html)
- Corrects **nonlinear distortion** caused by susceptibility  
- Requires **reversed phase-encoding b0 images**

#### [FSL's eddy](https://web.mit.edu/fsl_v5.0.10/fsl/doc/wiki/eddy(2f)UsersGuide.html)
- Corrects **linear distortion** from eddy currents & subject motion  
- Works best with **multiple DWIs per b-value**

#### DSI Studio: Motion Correction
- Corrects for **eddy current and motion artifacts**  
- Lightweight and integrated into `.src` workflow

---

### 🧩 Preprocessing Options

1. **FSL's `topup + eddy`** → most comprehensive  
2. **FSL's `eddy` only** → for datasets lacking reverse-phase b0  
3. **DSI Studio motion correction** → quick fix when others are unavailable  

---

### 🔮 Future Trend

🧠 *“Preprocessing is becoming less critical”* (my two cents)  
- Modern sequences reduce artifacts (Reese et al., MRM 2003; Jun 2024 [arXiv](https://arxiv.org/abs/2409.07375))  
- More **preprocessed open datasets** (e.g., HCP at the Fiber Data Hub) now available  

---

## 🧪 Hands-On Practice

### 🖐️ Hands-on 1: Explore Correction Effects
1. Download `.sz` files from [Fiber Data Hub – ds002087][ds002087]  
2. Compare `.sz` and `.fz` with/without correction  
3. Visualize **arcuate fasciculus** with vs. without corrections  

### 🖐️ Hands-on 2: Try FSL's Preprocessing Tools  
1. Download:  
   - [DWI NIfTI](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.nii.gz)  
   - [PA b0 image](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/fmap/sub-01_acq-multiband_dir-PA_dwi.nii.gz)  
   - [bval](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.bval), [bvec](https://s3.amazonaws.com/openneuro.org/ds003974/sub-01/dwi/sub-01_acq-multiband_dwi.bvec)  
2. Identify reversed-phase b0  
3. Run FSL’s **`topup` and `eddy`**

---

## 🧭 Session 3: Additional Preprocessing Steps (15 minutes)

### 🧬 When to Apply These Steps
Primarily for **animal studies** or **datasets with acquisition inconsistencies**.

---

### 🔧 Common Additional Steps

- ✅ **b-table correction**  
  - Especially important in **animal studies** due to gradient misalignment  
  - Ensures correct orientation of diffusion directions

- 🔄 **Flip/Swap image axes**  
  - Often needed for **non-human imaging** where scanner coordinate systems differ  
  - Use anatomical references to verify correct orientation

- 📏 **Regrid to isotropic resolution**  
  - Standardizes voxel dimensions (e.g., from 0.5×0.5×1 mm → 0.5 mm³)  
  - Improves downstream processing accuracy

---

### 🖐️ Hands-On Practice

📂 Dataset: [OpenNeuro ds005849](https://openneuro.org/datasets/ds005849)  
- Compare pre- and post-processed images  
- Test regridding and verify axis alignment  
- Explore effect on tractography (optional)

---


Here’s a clean and slide-ready version of **Session 3: Diffusion Modeling Methods**, with your "two cents" clearly framed, key facts emphasized, and content organized for a 15-minute talk:

---

## 🧭 Session 3: Diffusion Modeling Methods (15 minutes)

### 💡 My Two Cents: Angular Resolution Is Overrated

<img src="https://github.com/user-attachments/assets/8be66885-248f-42d6-ac73-47db336119b7" width="800" />

**FACT 1:**  
🧠 *High angular resolution cannot distinguish “kissing” vs. “crossing” fibers*  
→ Even with perfect data, DWI still cannot resolve this ambiguity.

**FACT 2:**  
🔬 *Higher **spatial** resolution can help differentiate “kissing” from “crossing” fibers*  
→ Adjacent tracts are more separable in smaller voxels.

**FACT 3:**  
📉 *Most datasets contain ~180 diffusion measurements with low SNR*  
→ Complex models tend to overfit quickly under these conditions.

---

### 🧭 Suggested Strategy for Modeling

- ✅ **Strategy 1:** Prioritize **spatial resolution** over angular resolution  
- ✅ **Strategy 2:** Use models that are **robust to noise** and **stable under low SNR**

---

<img src="https://github.com/user-attachments/assets/6f182387-1275-4070-b003-83828212894f" width="800" />

<img src="https://github.com/user-attachments/assets/4603498e-a769-432b-87fc-7d5145397105" width="800" />


### 🧰 DTI: 

- 🤔 *The limitation of the single tensor model is often exaggerated—especially at low resolution*  
- ⚠️ FA maps are unreliable at **low SNR**, yet often used uncritically  
- ✅ Still effective when paired with sufficient spatial resolution and smoothing

---

### 🧰 GQI / QSDR: 

- ⚠️ *Limited power for resolving complex crossing fibers*  
- 🧭 Mathematically, the **largest peak in GQI’s ODF** often matches the **tensor principal direction**  
- ✅ Main advantage: Provides a **robust anisotropy index** (QA) to guide fiber tracking

---

## Session 4: GUI-based Batch Processing (15 minutes)

