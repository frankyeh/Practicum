
# Session 1: Introducing DSI Studio (15 minutes)

DSI Studio is built for simplicity, transparency, and accessibility—providing researchers and clinicians with an intuitive platform for diffusion MRI tractography and connectome analysis.

• 🔧 Minimal Preprocessing  
DSI Studio follows a minimalist preprocessing philosophy, using only essential steps like FSL’s **TOPUP** and **eddy**. 

• 📈 Simple, Reliable Models  
The software supports models including **DTI**, **GQI**, and **QSDR**.

• 🔁 Actively Maintained and User-Driven  
Frequent updates reflect direct user feedback through the public forum. Most new features are developed in response to real research needs.

• 💡 Innovation Through Simplicity  
DSI Studio introduces clear, concept-driven methods such as tract-to-region connectome, differential tractography, and correlational tractography.  

## 1.1 DSI Studio Community Support

- Documentations: [https://dsi-studio.labsolver.org](https://dsi-studio.labsolver.org)
- Discussion group: [https://groups.google.com/g/dsi-studio](https://groups.google.com/g/dsi-studio) for bug report, suggestions, questions.
- Workshop: [https://practicum.labsolver.org](https://practicum.labsolver.org)
- Data: [https://brain.labsolver.org](https://brain.labsolver.org)

## 1.2 DSI Studio Version History

DSI Studio began as a research-focused tool—and it continues to evolve with that mission in mind. The software is actively maintained and updated, typically on a **weekly basis**.

### Version Timeline
- **Pre-"Chen" (2008–2022)**
- **"Chen" Era (2022–2024)**
- **"Hou" Era (2025–Present)**
- **Tip:**  
Keep a working copy of DSI Studio alongside your data, as the software is updated frequently (often daily!).

---

## 1.3 Setup & Installation

- **Windows:**  
Download and run directly—DSI Studio is a portable program and doesn’t require installation.

- **macOS (13+):**  
Download the app package, enable permissions, and bypass Gatekeeper (required for macOS 15+).

- **Ubuntu (20.04+):**  
Download the executable and run it directly—no installation needed.

- **Docker/Singularity:**  
Prebuilt containers are available. Just download and run for consistent and portable environments.

- **Recommended Hardware:**  
A desktop with a **multi-core CPU** and an **NVIDIA GPU** is recommended for faster processing and smoother rendering.

---

# Workshop Outline

### • Interface and Command History (WK1)  
The command history function records GUI operations and turns them into reusable command scripts. It helps automate workflows and ensures reproducible processing.

### • Fiber Data Hub (WK1)  
The Fiber Data Hub is a cloud platform providing instant access to over 37,000 preprocessed brain fiber datasets. It includes data from major studies like HCP, ABCD, and OpenNeuro, allowing researchers to explore brain connectivity without handling preprocessing.

---

### • Minimal Preprocessing Pipeline (WK2)  
Covers the recommended preprocessing steps for diffusion MRI data to prepare it for tractography, focusing on simplicity and compatibility with DSI Studio.

### • Fiber Tracking Basics (WK2)  
Introduces new metrics like **tract-to-voxel ratio** and **seed-to-voxel ratio**, which improve how tracts are counted and interpreted during fiber tracking.

---

### • Tractography on T1w/T2w/CT Images (WK3)  
Tractography can now be applied to structural images by registering them to diffusion space. This feature helps integrate clinical imaging with tractography analysis.

### • New Population-Averaged Templates (WK3)  
Newly generated average brain templates offer better spatial normalization and group comparisons across subjects.

### • Tract-to-Region Connectome (WK3)  
This method maps specific white matter tracts to brain regions, providing more anatomical detail than traditional region-to-region connectomes.

---

### • Differential and Correlational Tractography (WK4)  
These tools detect changes or correlations in white matter tracts across different groups or conditions, supporting studies in neurology, psychiatry, and brain development.

---

# Session 2: DSI Studio Interfaces (15 minutes)

## 2.1 Graphic-user Interface 

- Tractography Flow:

  Raw images (DICOM, NIFTI, etc.) 📂 ➝ .sz file (DWI signals + bval/bvec) 📊 ➝ .fz files ( fiber orientations + anisotropy) 🖼️ ➝ .tt.gz ( tractography) 🧠

<img src="https://github.com/user-attachments/assets/091b5dcd-093b-4a9c-a0d8-85c9c350a461" width="600"/>

- Console Window:

<img src="https://github.com/user-attachments/assets/9ef85f98-afad-44dd-a2ff-65ef66d52910" width="600"/>

## 2.2 Command-line Interface

- Loop functions:
 
reduce the need for writing bash scripts

## 2.3 Image viewer/editor

<img src="https://github.com/user-attachments/assets/925facea-61b3-4fa9-b350-b5df25b99d47" width="600"/>

# Session 3: Fiber Data Hub (10 minutes)

![image](https://github.com/user-attachments/assets/455a71b7-dc1b-4960-b2ba-401b6f70c1a9)

![image](https://github.com/user-attachments/assets/189aab8b-d7af-4992-af4b-22647ac2efc5)

# Session 4: Tractography Interfaces and Command History (15 minutes)



# Assignments


## Assignment 1. Screen capture whole brain tractography from 10 subjects using command history function


## Assignment 2: Batch Processing NIfTI Files to Reduce File Size

### Objective:  
Reduce the size of T1-weighted images by adjusting intensity, data type, and spatial resolution.

---

### **Step-by-Step Instructions:**

1. **Download the Dataset**  
   - Visit: [https://openneuro.org/datasets/ds001378](https://openneuro.org/datasets/ds001378)  
   - Click **[Download]**, then click the **[Download]** button again.  
   - Choose an output folder to save the files.

2. **Collect T1-Weighted Images**  
   - Navigate to the downloaded dataset’s `SCA2` folder.  
   - Search for all files named `*T1w.nii.gz` and copy them into a new working folder.

3. **Open Images in DSI Studio**  
   - Launch DSI Studio.  
   - Go to **[Tools] → [Step O1: View Images]**  
   - Select all `T1w.nii.gz` files in the folder.  
   - Note: DSI Studio will preview only the **first image**, but the actions will later apply to all.

4. **Adjust Image Contrast**  
   - In the top menu, go to:  
     - **[Views] → [Normalize Otsu Median]**  
     - **[Views] → [Upper Threshold]**, enter `1`

5. **Reduce Data Precision**  
   - In the top-right dropdown menu, change the image type from **32-bit floating point** to **8-bit integer**

6. **Downsample Image Volume**  
   - Go to **[Volume] → [Resize]**  
   - Enter new dimensions: `200 256 160`

7. **Save the Processed Images**  
   - Go to **[File] → [Save as...]**  
   - Use a new filename with a suffix, e.g., `*_T1w_reduced.nii.gz`

8. **Apply Settings to All Files**  
   - When prompted, click **[Yes]** to apply the same changes to all selected images.

9. **(Optional) Use Console to Automate the Task**  
   - Open the **console window** in DSI Studio to view the command log for each processing step.  
   - Use the generated command to apply the same operations via command line.

   #### Example command:
   ```bash
   dsi_studio --action=img --source=*.nii.gz --cmd="normalize_otsu_median+upper_threshold:1+change_type:0+resize:200 256 160" --output=../*_reduced.nii.gz
   ```

   This command batch-processes all `.nii.gz` images in the current folder and saves the reduced versions with a `_reduced` suffix in the parent directory.

---


