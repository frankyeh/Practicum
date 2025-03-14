
# Session 1: Introducing DSI Studio "Hou" "侯" version (15 min)

## Design paradigm

The Design Paradigm of DSI Studio:

- Razor Rule – DSI Studio provides a straightforward approach to tractography, making it accessible to researchers and clinicians. If a simple method works, the result is usually more robust.

- Minimal Preprocessing – DSI Studio follows a minimalist preprocessing philosophy, leveraging FSL’s TOPUP and eddy for essential corrections. The core idea is simple: if results require extensive preprocessing to be valid, they are unlikely to be strong or reproducible. (Even better if the results remain consistent without preprocessing!)

- Simple Modeling – DSI Studio prioritizes simple and reliable models, including DTI, GQI, and QSDR, ensuring robust results without excessive complexity.

- Adaptive to Research Needs – DSI Studio undergoes frequent updates to integrate user feedback, address emerging research challenges, and enhance functionality. This commitment ensures the tool remains relevant, responsive, and effective for the research community.

- Conceptual Approach Over Complexity – Rather than refining existing methodologies with more sophisticated techniques, DSI Studio focuses on developing new yet simple analysis concepts to advance brain research. Examples include:

  - Tract-to-region connectome – A method for analyzing brain connectivity at the tract level.
  - Differential tractography – A technique for detecting neurological changes due to disease or injury.
  - Correlational tractography – A method for studying the relationship between brain structure and external variables.

## DSI Studio Community Support

- Documentations: https://dsi-studio.labsolver.org
- Discussion group: https://groups.google.com/g/dsi-studio (2200 threads) for bug report, suggestions, questions.
- Workshop: https://practicum.labsolver.org
- Data: https://brain.labsolver.org

## Major Update from "Chen"

  - Fiber Data Hub

    [Link to the portal](https://brain.labsolver.org)
    
    The Fiber Data Hub is a cloud-based resource providing immediate access to over 37,000 preprocessed brain fiber datasets derived from diffusion MRI studies. Designed to support and accelerate tractography research, the hub hosts data from major neuroimaging projects, including the Human Connectome Project, Adolescent Brain Cognitive Development (ABCD) study, and all OpenNeuro repositories.
    ![image](https://github.com/user-attachments/assets/189aab8b-d7af-4992-af4b-22647ac2efc5)

  - Fiber tracking algorithms: tract-to-voxel ratio, seed-to-voxel ratio

  - Tract-to-region connectome:

    ![image](https://github.com/user-attachments/assets/6b263d74-3d54-4194-9f32-8af0acd32966)

    [Yeh, Fang-Cheng. "Population-based tract-to-region connectome of the human brain and its hierarchical topology." Nature communications 13.1 (2022): 4933.](https://www.nature.com/articles/s41467-022-32595-4)

    region-to-region connectomes depict connections between distinct brain areas, often without detailing the specific white matter pathways involved. In contrast, tract-to-region connectomes map the precise white matter tracts connecting to particular brain regions, offering a more detailed understanding of the structural pathways underlying these connections

  - Tractography in T1w/T2w/CT images
    
  - New population-averaged templates



# Session 2 Graphic-user interface (15 minutes)

- Tractography Flow:

  Raw images (DICOM, NIFTI, etc.) 📂 ➝ .sz file (DWI signals + bval/bvec) 📊 ➝ .fz files ( fiber orientations + anisotropy) 🖼️ ➝ .tt.gz ( tractography) 🧠

  ![image](https://github.com/user-attachments/assets/091b5dcd-093b-4a9c-a0d8-85c9c350a461)

- Image viewer/editor

  ![image](https://github.com/user-attachments/assets/925facea-61b3-4fa9-b350-b5df25b99d47)

- Image linear and nonlinear registration

  ![image](https://github.com/user-attachments/assets/363d318f-67a4-47b9-8e5b-5d4d568905a4)


# Session 3 Command-line interface (15 minutes)

- Console:

  ![image](https://github.com/user-attachments/assets/9ef85f98-afad-44dd-a2ff-65ef66d52910)




