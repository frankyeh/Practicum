
# Session 1: Introducing DSI Studio "Hou" "侯" version (15 min)
![image](https://github.com/user-attachments/assets/091b5dcd-093b-4a9c-a0d8-85c9c350a461)

## Design paradigm

The Design Paradigm of DSI Studio:

- Razor Rule – DSI Studio provides a straightforward approach to tractography, making it accessible to researchers and clinicians. If a simple method works, there is no need for unnecessary complexity. For those requiring more advanced modeling techniques, tools like MRtrix and DIPY are available.

- Minimal Preprocessing – DSI Studio follows a minimalist preprocessing philosophy, leveraging FSL’s TOPUP and eddy for essential corrections. No additional preprocessing is included. The core idea is simple: if results require extensive preprocessing to be valid, they are unlikely to be strong or reproducible. (Even better if the results remain consistent without preprocessing!)

- Simple Modeling – DSI Studio prioritizes simple and reliable models, including DTI, GQI, and QSDR, ensuring robust results without excessive complexity.

- Adaptive to Research Needs – DSI Studio undergoes frequent updates to integrate user feedback, address emerging research challenges, and enhance functionality. This commitment ensures the tool remains relevant, responsive, and effective for the research community.

- Conceptual Approach Over Complexity – Rather than refining existing methodologies with more sophisticated techniques, DSI Studio focuses on developing new yet simple analysis concepts to advance brain research. Examples include:

  - Tract-to-region connectome – A method for analyzing brain connectivity at the tract level.
  - Differential tractography – A technique for detecting neurological changes due to disease or injury.
  - Correlational tractography – A method for studying the relationship between brain structure and external variables.

## Major Update from "Chen"

  - Fiber Data Hub
    ![image](https://github.com/user-attachments/assets/189aab8b-d7af-4992-af4b-22647ac2efc5)

  - Fiber tracking algorithms: tract-to-voxel ratio, seed-to-voxel ratio
  - Tract-to-region connectome:
    [Yeh, Fang-Cheng. "Population-based tract-to-region connectome of the human brain and its hierarchical topology." Nature communications 13.1 (2022): 4933.](https://www.nature.com/articles/s41467-022-32595-4)
    ![image](https://github.com/user-attachments/assets/6b263d74-3d54-4194-9f32-8af0acd32966)

  - Tractography atlas in T1w/T2w images
  - Revised templates

## DSI Studio Community Support

- Documentations: dsi-studio.labsolver.org
- Discussion group:
- Fiber data hub:


# Session 2 Graphic-user interface (15 minutes)

- Tractography Flow:

- Image viewer/editor

- Image registration and normalization


# Session 3 Command-line interface (15 minutes)

- Console:

  ![image](https://github.com/user-attachments/assets/9ef85f98-afad-44dd-a2ff-65ef66d52910)




