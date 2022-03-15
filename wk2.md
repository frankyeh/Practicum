# Week 2 Automatic Fiber Tracking

Linggang Luo/Fang-Cheng Yeh

---

## Before practicum on Friday, please complete following:

### Watch [Dr. Schneider's TED Talk]

<iframe width="896" height="504" src="https://www.youtube.com/embed/su-uRdPTpEY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Anatomy

- In DSI-Studio white matter atlas, pathways can be catogorized as 3 major types: commissural, association and prjection pathways.

    - Commisural pathways: anterior commissure and corpus callosum

    - Projection pathways: acoustic radiation, corticobulbar tract, corticopontine tract (frontal, parietal, and occipital), corticostriatal tract(anterior, superior and posterior), corticospinal tract, dentatorubrothalamic tract, fornix, medial lemniscus, optic radiation, reticulospinal tract, and thalamic radiation (anterior, posterior and superior)
    
    - Association pathways: arcuate fasciculus, cingulum(frontal parahippocampal, frontal parietal, parahippocampal parietal, parahippocampal, and parolfactory), extreme capsule, frontal aslant, inferior fronto-occipital fasciculus, inferior longitudinal fasciculus, middle longitudinal fasciculus, parietal aslant tract, superior longitudinal fasciculus (I, II and III), uncinate fasciculus, and vertical occipital fasciculus

- Read through ***[Overview of White Matter Tracts- Commissural Pathways](https://drive.google.com/file/d/1gq0uCRHmOKP9zp7uEKBH3rMIrvbivA8N/view?usp=sharing)***.

- Read through ***[Overview of White Matter Tracts- Perisylvian Pathways](https://drive.google.com/file/d/1arn8hbdF8YP6j09Gq6Z1ip2PITbMwzoo/view?usp=sharing)***. Note that perisylvian pathways is a subdivision of association pathways.

- A review on recent known and unknown about white matter pathways: [Bullock DN, Hayday EA, Grier MD, Tang W, Pestilli F, Heilbronner S. A taxonomy of the brain’s white matter: Twenty-one major tracts for the twenty-first century.](psyarxiv.com/fvk5r/)

### DSI-Studio

#### Read through ***[HDFT Pipeline](https://drive.google.com/file/d/1I3HZT_SGo680efozNhpf60Oes1ErSkz2/view?usp=sharing)***.


---


## During practicum on Friday:


- Introduction to white matter pathways mentioned above.

- Introduction to DSI Studio (reconstruction, fiber tracking).

- Diffusion MRI quality control:

<iframe width="896" height="504" src="https://www.youtube.com/embed/stL4GMeTC1I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- Manual track editing:

<iframe width="896" height="504" src="https://www.youtube.com/embed/1xfhaFQhCtY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Practicum task:

1. Point out susceptibility artifact in FA map and raw image.

2. Manually select cingulum pathways from whole brain track.

---

### Practicum task 1: Generate and reconstruct SRC files

1. Download subject (A00008326)'s dwi data from https://openneuro.org/datasets/ds001021/versions/1.0.0 (under SES-DS2), including *.nii.gz and .bval and .bvec.

2. [Generate SRC file](http://dsi-studio.labsolver.org/doc/gui_t1.html) and check if there are artifacts [(youtube)](https://www.youtube.com/embed/stL4GMeTC1I).

3. [Reconstruct the SRC file using DTI and GQI](http://dsi-studio.labsolver.org/doc/gui_t2.html).

### Practicum task 2: Manual tract segmentation

1. Run [whole brain fiber tracking](http://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html) on each FIB file.

2. Manually select left arcuate fasciculus from whole brain tracks (on DTI and GQI fib files). 

3. Segment left arcuate fasciculus into the acoustic, visual, and lexical encoding part and assign different colors, as done in [a review study](https://doi.org/10.1093/brain/awac057)

### Practicum task 3: Automated fiber tracking

3. Run [automatic fiber tracking](http://dsi-studio.labsolver.org/doc/gui_t3_atk.html) on left arcuate fasciculus and compare it with manual result (on DTI and GQI fib files).

4. Compare their differences in FA/QA map and tractogram (on DTI and GQI fib files).

