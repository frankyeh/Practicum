# Week 2 Guidance

Linggang Luo

*January 2022*

Some materials will be shared via our [google drive folder](https://drive.google.com/drive/folders/12XGKtBVUb7i-uW_LSkMERFRhP7S95OrQ?usp=sharing) for confidentiality reasons.

---



## Before practicum on Friday, please complete following:

### Watch [Dr. Schneider's TED Talk]

<iframe width="1120" height="630" src="https://www.youtube.com/embed/su-uRdPTpEY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Anatomy

- In DSI-Studio white matter atlas, pathways can be catogorized as 3 major types: commissural, association and prjoction pathways:
    - Commisural pathways: anterior commissure and corpus callosum

    - Projection pathways: acoustic radiation, corticobulbar tract, corticopontine tract (frontal, parietal, and occipital), corticostriatal tract(anterior, superior and posterior), corticospinal tract, dentatorubrothalamic tract, fornix, medial lemniscus, optic radiation, reticulospinal tract, and thalamic radiation (anterior, posterior and superior)
    
    - Association pathways: arcuate fasciculus, cingulum(frontal parahippocampal, frontal parietal, parahippocampal parietal, parahippocampal, and parolfactory), extreme capsule, frontal aslant, inferior fronto-occipital fasciculus, inferior longitudinal fasciculus, middle longitudinal fasciculus, parietal aslant tract, superior longitudinal fasciculus (I, II and III), uncinate fasciculus, and vertical occipital fasciculus

- Read through ***[Overview of White Matter Tracts- Commissural Pathways](https://drive.google.com/file/d/1gq0uCRHmOKP9zp7uEKBH3rMIrvbivA8N/view?usp=sharing)***.

- Read through ***[Overview of White Matter Tracts- Perisylvian Pathways](https://drive.google.com/file/d/1arn8hbdF8YP6j09Gq6Z1ip2PITbMwzoo/view?usp=sharing)***. Note that perisylvian pathways is a subdivision of association pathways.



### DSI-Studio

#### Read through ***[HDFT Pipeline](https://drive.google.com/file/d/1I3HZT_SGo680efozNhpf60Oes1ErSkz2/view?usp=sharing)***.

#### Delineate thalamus in DSI-Studio

- Download [100206.src.gz.gqi.1.25.fib.gz](https://drive.google.com/file/d/1l4Qvyf1FHsLGKQs2axVYqcbBo7Hv2Kox/view?usp=sharing) and [100206_T1w.nii.gz](https://drive.google.com/file/d/1S_j00jZgq7YhMCz6XiM_gwG1zajkZrhu/view?usp=sharing) from google drive.

- Load 100206.src.gz.gqi.1.25.fib.gz onto DSI-Studio.

- Load 100206_T1w.nii.gz by clicking on ***"Insert Other Images"*** under ***Slices*** menu.

- According to the video of ***["quick 3D manual segmentation of a brain tumor"](https://www.youtube.com/watch?v=ZkWBU_qnaKg&t=1s)***, draw an ROI of left thalamus.

- Open atlases, choose FreeSurferDKT subcortical atlas, and load left thalamus.

- Compare your thalamus ROI to that of FreeSurferDKT subcortical atlas.

---


## During practicum on Friday:

- Dr. Yeh's Q&A.

- Introduction to white matter pathways mentioned above.

- Introduction to DSI Studio (reconstruction, fiber tracking).

- Diffusion MRI quality control:

<iframe width="560" height="315" src="https://www.youtube.com/embed/stL4GMeTC1I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


- Manual track editing:

<iframe width="560" height="315" src="https://www.youtube.com/embed/1xfhaFQhCtY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---


### Practicum task 1: Generate and Reconstruct SRC files

1. Download subject (A00008326)'s dwi data from https://openneuro.org/datasets/ds001021/versions/1.0.0 (under SES-DS2), including *.nii.gz and .bval and .bvec.
2. [Generate SRC file](http://dsi-studio.labsolver.org/doc/gui_t1.html) and check if there are artifacts [(youtube)](https://www.youtube.com/embed/stL4GMeTC1I).
3. [Reconstruct the SRC file using DTI and GQI](http://dsi-studio.labsolver.org/doc/gui_t2.html).
4. Reconstruct eddy-corrected SRC file using DTI and GQI.

### Practicum task 2: Mapping pathways

1. Run [whole brain fiber tracking](http://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html) on each FIB file.
2. Manually select left arcuate fasciculus from whole brain tracks (on DTI and GQI fib files). 
3. Run [automatic fiber tracking](http://dsi-studio.labsolver.org/doc/gui_t3_atk.html) on left arcuate fasciculus and compare it with manual result (on DTI and GQI fib files).
4. Compare their differences in FA/QA map and tractogram (on DTI and GQI fib files).

### Practicum test:

1. Point out susceptibility artifact in raw image.
2. Point out which FA map has eddy current artifact.
3. Manually select cingulum pathways from whole brain track.
