# White Matter Tracts & Virtual Dissection

## Before practicum on Friday, please complete following:

### White Matter Anatomy 

- Reading: a review on recent known and unknown about white matter pathways: [Bullock DN, Hayday EA, Grier MD, Tang W, Pestilli F, Heilbronner S. A taxonomy of the brain’s white matter: Twenty-one major tracts for the twenty-first century.](https://psyarxiv.com/fvk5r/)

- Video: [Computational Neuroanatomy at DIPY Workshop](https://www.youtube.com/watch?v=0gffgCBDOfk)

- White matter pathways can be catogorized into commissural, association, and prjection pathways.

    - Commissural pathways: anterior commissure and corpus callosum

    - Projection pathways: acoustic radiation, corticobulbar tract, corticopontine tract (frontal, parietal, and occipital), corticostriatal tract(anterior, superior and posterior), corticospinal tract, dentatorubrothalamic tract, **fornix**, medial lemniscus, optic radiation, reticulospinal tract, and thalamic radiation (anterior, posterior and superior)
    
    - Association pathways: arcuate fasciculus, cingulum (frontal parahippocampal, frontal parietal, parahippocampal parietal, parahippocampal, and parolfactory), extreme capsule, frontal aslant, inferior fronto-occipital fasciculus, inferior longitudinal fasciculus, middle longitudinal fasciculus, parietal aslant tract, superior longitudinal fasciculus (I, II and III), uncinate fasciculus, and vertical occipital fasciculus


---

## During practicum on Friday:

- Introduction to white matter pathways

  - Hands-on (Frank)
    - [HCP1065 Group-average template 1mm](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1)
    - [Tractography atlas](https://pitt-my.sharepoint.com/:f:/g/personal/yehfc_pitt_edu/EjD1HZDMSnVGuuXm_B5vczQBuvY8WFjtHQR-AnXQc6izvQ?e=JIOLDz)

  - White matter tract anatomy (Linggang)  
  
- Virtual dissection

  - Hands-on (Frank)
    - [HCP1065 Group-average template 1mm](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1)
    - [Whole brain fiber tracking & Track dissection](https://dsi-studio.labsolver.org/doc/gui_t3_whole_brain.html)

<iframe width="896" height="504" src="https://www.youtube.com/embed/1xfhaFQhCtY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- Automatic Fiber Tracking

  - Hands-on (Linggang)
    - [HCP1065 Group-average template 1mm](https://zenodo.org/record/6324701/files/HCP1065.1mm.fib.gz?download=1)
    - [Automatic fiber tracking](https://dsi-studio.labsolver.org/doc/gui_t3_atk.html)
   
<iframe width="896" height="504" src="https://www.youtube.com/embed/Hzeb_q6ux-Q" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Assignment:

Manually select white matter pathways from whole brain tractogram.

### task 1: Download FIB file

1. Download [100206.src.gz.gqi.1.7.fib.gz](https://zenodo.org/record/6307812/files/100206.src.gz.gqi.1.7.fib.gz?download=1) 

2. Open the FIB file using [Step T3 Fiber Tracking] and click on [Step T3d Tracts][Fiber Tracking] to generate whole brain tracts 

### task 2: Manual tract segmentation

1. Manually segment **left arcuate fasciculus**, **cingulum**, **uncinate fasciculus**, **corticospinal tract** from whole brain tracks. Compare it with automatic tracking results.

2. Segment left arcuate fasciculus into the acoustic, visual, and lexical encoding part and assign different colors (reference: Giampiccolo D, Duffau H. Controversy over the temporal cortical terminations of the left arcuate fasciculus: a reappraisal. Brain. 2022 Feb 10.)

![image](https://user-images.githubusercontent.com/275569/165971411-eeab4e61-f356-4456-b582-627a05f778da.png)
(Giampiccolo et al. 2022)

<img src="https://user-images.githubusercontent.com/275569/165971142-40f86637-b727-47da-9e8d-2ffa2338f70f.png" width=500>
(Segmented on HCP1065 tractography atlas)



