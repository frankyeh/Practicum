# DSI Studio 2025 Workshop Outline

- 🧭 Workshop Format

Each workshop will run for 1 hour, divided into four 15-minute sections. During each section, feel free to drop your questions in the Zoom chat at any time. I’ll go through them one by one during the short breaks between sections.

- 🎥 Recordings

The sessions will be recorded and posted on YouTube afterward. If you prefer, you’re welcome to just watch the recordings instead of attending live—live participation is mainly for real-time interaction.

- 🙋‍♂️ Post-Workshop Q&A (Unrecorded)

After each session, we’ll have an informal, off-the-record Q&A. You can ask about your own research, bring up ideas, or suggest features you'd like to see in DSI Studio. It’s an open forum to chat and brainstorm together.

---

### • Interface and Command History (WK1)  
The command history function records GUI operations and turns them into reusable command scripts. It helps automate workflows and ensures reproducible processing.

### • Fiber Data Hub (WK1)  
The Fiber Data Hub is a cloud platform providing instant access to over 37,000 preprocessed brain fiber datasets. It includes data from major studies like HCP, ABCD, and OpenNeuro, allowing researchers to explore brain connectivity without handling preprocessing.

### • Minimal Preprocessing Pipeline (WK2)  
Covers the recommended preprocessing steps for diffusion MRI data to prepare it for tractography, focusing on simplicity and compatibility with DSI Studio.

### • Fiber Tracking Basics (WK2)  
Introduces new metrics like **tract-to-voxel ratio** and **seed-to-voxel ratio**, which improve how tracts are counted and interpreted during fiber tracking.

### • Tractography on T1w/T2w/CT Images (WK3)  
Tractography can now be applied to structural images by registering them to diffusion space. This feature helps integrate clinical imaging with tractography analysis.

### • New Population-Averaged Templates (WK3)  
Newly generated average brain templates offer better spatial normalization and group comparisons across subjects.

### • Tract-to-Region Connectome (WK3)  
This method maps specific white matter tracts to brain regions, providing more anatomical detail than traditional region-to-region connectomes.

### • Differential and Correlational Tractography (WK4)  
These tools detect changes or correlations in white matter tracts across different groups or conditions, supporting studies in neurology, psychiatry, and brain development.

---

# Session 1: Introducing DSI Studio (15 minutes)

DSI Studio is built for simplicity, transparency, and accessibility—providing researchers and clinicians with an intuitive platform for diffusion MRI tractography and connectome analysis.

## 1.1 Design Paradigm

• 🔧 Minimal Preprocessing  
DSI Studio follows a minimalist preprocessing philosophy, using only essential steps like FSL’s **TOPUP** and **eddy**. 

• 📈 Diffusion Models  
The software supports models including **DTI**, **GQI**, and **QSDR**.

• 🔁 Actively Maintained and User-Driven  
Frequent updates reflect direct user feedback through the public forum. Most new features are developed in response to real research needs.

• 💡 Concept-driven Methods  
DSI Studio introduces concept-driven methods such as tract-to-region connectome, differential tractography, and correlational tractography.  

## 1.2 Community Support

- Website: [https://dsi-studio.labsolver.org](https://dsi-studio.labsolver.org)
  - Download links
  - Documentation
  - Links to other support websites
- Discussion group: [https://groups.google.com/g/dsi-studio](https://groups.google.com/g/dsi-studio)
  - Bug report
  - Suggestions
  - Questions
- Workshop: [https://practicum.labsolver.org](https://practicum.labsolver.org)
  - Tutorial videos
- Data: [https://brain.labsolver.org](https://brain.labsolver.org)
  - Tractography atlases
  - Templates
  - Individual scan data
    
## 1.3 Version History

DSI Studio began as a research-focused tool—and it continues to evolve with that mission in mind. The software is actively maintained and updated, typically on a **weekly basis**.

- **Pre-"Chen" (2008–2022)**
- **"Chen" (2022–2024)**
- **"Hou" (2025–Present)**

**Keep a working copy of DSI Studio alongside your data, as the software is updated frequently (often daily!).**

## 1.4 Setup & Installation

- **Recommended Hardware:**  
A desktop with a **multi-core CPU** and an **NVIDIA GPU** is recommended for faster processing and smoother rendering.

- **Windows:**  
Download and run directly—DSI Studio is a portable program and doesn’t require installation.

- **macOS (13+):**  
Download the app package, enable permissions, and bypass Gatekeeper (required for macOS 15+).

- **Ubuntu (20.04+):**  
Download the executable and run it directly—no installation needed.

- **Docker/Singularity:**  
Prebuilt containers are available. Just download and run for consistent and portable environments.

---

# Session 2: DSI Studio Interfaces (15 minutes)

## 2.1 Graphic-user Interface 

### Console Window:

<img src="https://github.com/user-attachments/assets/9ef85f98-afad-44dd-a2ff-65ef66d52910" width="600"/>

 - Displays internal messages and system logs
 - Allows users to run command-line instructions directly within the GUI

### Tractography Tabs:

<img src="https://github.com/user-attachments/assets/091b5dcd-093b-4a9c-a0d8-85c9c350a461" width="600"/>

  Raw images (DICOM, NIFTI, etc.) 📂 ➝ .sz file (DWI signals + bval/bvec) 📊 ➝ .fz files ( fiber orientations + anisotropy) 🖼️ ➝ .tt.gz ( tractography) 🧠

File Formats:

  - NIFTI: .nii.gz
  - SRC: .sz (or .src.gz in older versions)
  - FIB: .fz (or .fib.gz in older versions)
  - Tractography: .tt.gz (DSI Studio), .trk.gz (TrackVis)

### Other Tabs:

---

# Session 3: Fiber Data Hub (10 minutes)

<img src="https://github.com/user-attachments/assets/455a71b7-dc1b-4960-b2ba-401b6f70c1a9" width="600"/>

<img src="https://github.com/user-attachments/assets/189aab8b-d7af-4992-af4b-22647ac2efc5" width="600"/>

**Overview:**  
The Fiber Data Hub is a growing repository of preprocessed diffusion MRI data designed for ease of access and integration with DSI Studio.

**Key Features:**  
- Includes data from major projects: **HCP, ABCD, OpenNeuro**, and others  
- Covers both **human and animal brain scans**  
- **Continuously expanding** with community contributions  
- **Hosted independently** of DSI Studio on GitHub  
- Accessible via the **GitHub API**  
- Supports sharing of:  
  - **FIB files (.fz)** for tractography and fiber visualization  
  - **SRC files (.sz)** (when licensing permits)

---

Let me know if you want to add a link to the data hub or a quick demo script!
---

# Session 4: Tractography Interfaces (20 minutes)

<img src="https://github.com/user-attachments/assets/f3dd7fcc-3871-44d4-88af-3e7b6feb2ae3" width="600"/>

- Sample Data: [OpenNeuro][ds004299][sub-103]
- 3D Window & Shortcuts
  **views**
  - left button	to rotate view
  - right button to zoom in/out view
  - middle button or arrow keys	to move view
  - wheel	to zoom in/out view
  - Alt+1, Alt+2,…etc	remember the current viewport and slice position to memory slot 1
  - “1”, “2”,…etc.	return to the viewport and slice position recorded in memory slot 1
  
  **slices**    
  - Any	“Q” and “A”	move sagittal slide
  - Any	“W” and “S”	move coronal slide
  - Any	“E” and “D”	move axial slide
  - Any	“Z”	switch to sagittal view
  - Any	“X”	switch to coronal view
  - Any	“C”	switch to axial view

  **regions**
  - double left-clicks on a region to select it in the region list
  - Ctrl+A to drag a slice or a region in the 3D window.

- ROI Window & Shortcuts
  - right double click	 move slices to the pointed location.
  - middle button	drag a slice or a region in the ROI window.
  - wheel	zoom in or zoom out

- Method Window
- Tract Window
  - Tracking button
  - Autotrack
  - Tract Menu
  
- Region and ROI Window
  - ROI tools
  - Atlas function
  - Region Menu

- Settings & Rendering
  - Slice, Region, Tract, Device renderings

- Top Menu Functions
  - Workspace
  - Tract Editing
  - Region Editing
  - Tract Coloring & Recognition
  - Slices & Segmentation
  - Device
  - Screen Saving
  - Command History

---

# Assignments

## Assignment 1. Screen capture whole brain tractography from 10 subjects using command history function

1. ** Download all subjects's first session gqi.fz files from OpenNeuro ds000244 (Individual Brain Charting)
  - Open [Fiber Data Hub] → Repository: [OpenNeuro] → [ds000244]
  - Click on [Select Matching] button → gqi.fz (After entering the filter, move the scroll bar a bit to see the selected data)
  - Specify the Save Directory and Click on [Download 12 File(s)]

2. Screen capture whole brain tractography on downloaded files
  - At main window's [Tractography] tab, click on [Step T3: Fiber Tracking] and select the downloaded file `sub-01_ses-00_dwi.gqi.fz`
  - Click on the [Fiber Tracking] button on the right to get whole brain tractography
  - Adjust zoom value in the 3D window to get a good view
  - On the top menu, save whole brain tractography using [Screen][Save 3D Screen]  →  save screen shot as `sub-01_ses-00_dwi_whole_brain_screen.jpg`
  - On the top menu, select [Records][Command History]  →  Select all steps from `open_fib` to `save_screen`  →  Click [Apply to Others...] → Select other .fz files
  - On the top menu, select [File][Open FIB Directory] to see if the screenshots are generated.

---

## Assignment 2: Batch Processing NIfTI Files to Reduce File Size

### Objective:  
Reduce the size of T1-weighted images by adjusting intensity, data type, and spatial resolution.

### **Step-by-Step Instructions:**

1. **Download the Original OpenNeuro ds001378 Dataset**  
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


---

## Assignment 3: Command Line Batch Processing NIfTI Files to Reduce File Size

1. Open the **console window** in DSI Studio
  
2. Repeat the steps in Assignment 2 to identify the commands and parameter used in NIFTI tool.
   - The command usually has this format `name of the command`:`parameters`
   - For example, if regrid at 1 1 1, the name of the command is `regrid` and the parameters are `1 1 1`
    
3. Use command line to repeat the task of the assignment 2 

   Example command:
   
   ```bash
   dsi_studio --action=img --source=*.nii.gz --cmd="flip_x+upper_threshold:1+change_type:1" --output=../*_modified.nii.gz
   ```

   This command batch-processes all `.nii.gz` images in the current folder by flip the image at x direction, thresholded values beflow 1, and change the pixel type to 16-bit integer before sacing the results with a `_modified` suffix in the parent directory.

---


