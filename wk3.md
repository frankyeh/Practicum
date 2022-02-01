# Week 3 Guidance

Linggang Luo

*January 2022*

Some materials will be shared via our [google drive folder](https://drive.google.com/drive/folders/12XGKtBVUb7i-uW_LSkMERFRhP7S95OrQ?usp=sharing) for confidentiality reasons.


---


## Before practicum on Friday, please complete following:

### Anatomy

- Read through [Overview of White Matter Tracts - Limbic Pathways](https://drive.google.com/file/d/1YJMb8yeKxmFG5b8f7PrA9GQ--H4OnBxE/view?usp=sharing), [Overview of White Matter Tracts - Projection Pathways](https://drive.google.com/file/d/1IUyredH2rEBrBNBDDKgI0_Bm-pXlz5M3/view?usp=sharing) and [Overview of White Matter Tracts - Occipital Visual Pathways](https://drive.google.com/file/d/1IXLd6TMpu6dpzWhcwv7NwlUMTErnMTFO/view?usp=sharing).

- ***Perisylvian***, ***limbic*** and ***occipital visual*** pathways are categorized by their functions.
    - Perisylvian pathways: Arcuate fasciculus, superior longitudinal fasciculus (SLF), and frontal aslant.
    - Limbic pathways: Fornix, cingulum, and uncinate fasciculus.
    - Occipital visual pathways: Optic radiations, frontal occipital fasciculus (FOF), and inferior logitudinal fasciculus (ILF).


### DSI-Studio

#### Genrating left arcuate fasciculus raw tracts

- Down load [Region Manual](https://drive.google.com/file/d/1LZTUz2-dybD8LHrZNrnFimXHKWxAG8DK/view?usp=sharing) of [Schneider lab](https://www.lrdc.pitt.edu/schneiderlab/), and fib file [100206.src.gz.gqi.1.25.fib.gz](https://drive.google.com/file/d/1l4Qvyf1FHsLGKQs2axVYqcbBo7Hv2Kox/view?usp=sharing) from shared folder.

- Load the fib file on DSI-Studio by click "StepT3: Fiber Tracking & Visualization".

- According to page 17 of the Region Manual, in order to generate raw left arcuate fasciculus, we need to draw regions of interests (ROI) and regions of avoidance (ROA):
    - ROIs: ArcuateCoronal_left and ArcuateAxial_left
    - ROAs: SagittalROA, TemporalCoronal_left, InternalCapsule_left, ExternalCapsule_left, Midbody, InferiorOccipital_left and SFG_left

- To draw region ArcuateCoronal_left, for example, steps include:
1. Look up ***Table of Contents*** in page 2, find ***Regions*** - ***ArcuateCoronal_SIDE (AC)*** - ***page 63***.
2. Turn to page 63, follow the instructions of how to draw ArcuateCoronal_SIDE to identify the region looked for. Details of how to create regions are introduced in this [tutorial](https://dsi-studio.labsolver.org/doc/gui_t3_roi_tracking.html).
3. Remember to define the type of the region drawn, either ROI or ROA in the GUI. In the region window, click ***Type*** and then select ***ROI/ROA***.
4. After creating all the ROIs and ROAs, hit ***Fiber Tracking*** in the ***Tracts*** window.


---


## During practicum on Friday:

- Dr. Yeh's Q&A.

- Introduction to white matter pathways mentioned above.

- Demonstration of how to generate the raw left arcuate fasciculus.


---


### Practicum task 1: Draw ROIs and ROAs for generating raw tracts of corpus callosum (body)
1. Using manual to identify which regions need to be draw.
2. According to manual, draw those ROIs and ROAs correspondingly.

### Practicum task 2: Generate raw tracts of corpus callosum (body) and compare to auto-tracts
1. Fiber tracking with regions drawn above.
2. Uncheck all the regions and using auto-tracking function to generate auto-tracts.
3. Compare your tract with auto-tracts.