
# Session 1: Introducing DSI Studio (15 minutes)

## 🧭 DSI Studio Design Philosophy

DSI Studio is built for simplicity, transparency, and accessibility—providing researchers and clinicians with an intuitive platform for diffusion MRI tractography and connectome analysis.

### 🔧 Minimal Preprocessing  
DSI Studio follows a minimalist preprocessing philosophy, using only essential steps like FSL’s **TOPUP** and **eddy**. 

### 📈 Simple, Reliable Models  
The software supports established models like **DTI**, **GQI**, and **QSDR** to deliver dependable results without excessive complexity.

### 🔁 Actively Maintained and User-Driven  
Frequent updates reflect direct user feedback through the public forum. Most new features are developed in response to real research needs.

### 💡 Innovation Through Simplicity  
DSI Studio introduces clear, concept-driven methods that open new avenues for analysis:
- **Tract-to-Region Connectome** – tract-level connectivity mapping  
- **Differential Tractography** – detecting changes in white matter integrity  
- **Correlational Tractography** – linking fiber structure with behavioral or clinical variables  

## DSI Studio Community Support

- Documentations: https://dsi-studio.labsolver.org
- Discussion group: https://groups.google.com/g/dsi-studio for bug report, suggestions, questions.
- Workshop: https://practicum.labsolver.org
- Data: https://brain.labsolver.org

## 🔄 DSI Studio Version History

DSI Studio began as a research-focused tool—and it continues to evolve with that mission in mind. The software is actively maintained and updated, typically on a **weekly basis**.

### Version Timeline
- **Pre-"Chen" (2008–2022)**
- **"Chen" Era (2022–2024)**
- **"Hou" Era (2025–Present)**

## Setup & Installation

- Windows: download and run. portable program.
- MacOS(13+): download the app package, enable permission, bypass gatekeeper (15+)
- Ubuntu (20.04+): download and run
- Docker, singularity: download and run
  
- Recommended hardware: a desktop with multi-core CPU and a NVIDIA-GPU
- Keep a working copy with your data (DSI Studio updates on a daily basis!).

## Major Update from "Chen" Versions

- Fiber Data Hub

![image](https://github.com/user-attachments/assets/455a71b7-dc1b-4960-b2ba-401b6f70c1a9)

[Fiber Data Hub](https://brain.labsolver.org) is a cloud-based resource providing immediate access to over 37,000 preprocessed brain fiber datasets derived from diffusion MRI studies. Designed to support and accelerate tractography research, the hub hosts data from major neuroimaging projects, including the Human Connectome Project, Adolescent Brain Cognitive Development (ABCD) study, and all OpenNeuro repositories.

    ![image](https://github.com/user-attachments/assets/189aab8b-d7af-4992-af4b-22647ac2efc5)

- Command history: command history
  
- Fiber tracking algorithms: introduce tract-to-voxel ratio, seed-to-voxel ratio

- Tract-to-region connectome:

region-to-region connectomes depict connections between distinct brain areas, often without detailing the specific white matter pathways involved. In contrast, tract-to-region connectomes map the precise white matter tracts connecting to particular brain regions, offering a more detailed understanding of the structural pathways underlying these connections

![image](https://github.com/user-attachments/assets/6b263d74-3d54-4194-9f32-8af0acd32966)

[Yeh, Fang-Cheng. "Population-based tract-to-region connectome of the human brain and its hierarchical topology." Nature communications 13.1 (2022): 4933.](https://www.nature.com/articles/s41467-022-32595-4)

- Tractography in T1w/T2w/CT images
    
- New population-averaged templates


# Session 2 Interfaces (15 minutes)

## Graphic-user Interface 

- Tractography Flow:

  Raw images (DICOM, NIFTI, etc.) 📂 ➝ .sz file (DWI signals + bval/bvec) 📊 ➝ .fz files ( fiber orientations + anisotropy) 🖼️ ➝ .tt.gz ( tractography) 🧠

  ![image](https://github.com/user-attachments/assets/091b5dcd-093b-4a9c-a0d8-85c9c350a461)

## Command-line Interface

- Console Window:

![image](https://github.com/user-attachments/assets/9ef85f98-afad-44dd-a2ff-65ef66d52910)

- Loop functions:
 
reduce the need for writing bash scripts

## Command history


## Image viewer/editor

  ![image](https://github.com/user-attachments/assets/925facea-61b3-4fa9-b350-b5df25b99d47)

## Image linear and nonlinear registration

  ![image](https://github.com/user-attachments/assets/363d318f-67a4-47b9-8e5b-5d4d568905a4)





# Assignments


Assignment 1. Screen capture whole brain tractography from 10 subjects using command history


## 🧪 Assignment 2: Batch Processing NIfTI Files to Reduce File Size

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


