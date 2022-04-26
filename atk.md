# Diffusion MRI Processing & Automatic Fiber Tracking

## Before practicum on Friday, please complete following:

### Watch [Dr. Schneider's TED Talk]

<iframe width="896" height="504" src="https://www.youtube.com/embed/su-uRdPTpEY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Diffusion MRI basics

- Read through Dr. Yeh's [review paper](Materials/paper/review.pdf) on diffusion MRI, which also can be found under the shared folder. Pay special attention to part 3 (tractography methods), 5.2 (model-free methods), part 6 (fiber tracking methods) and part 7 (DTI tractography in brain tumors).

---

## During practicum on Friday:

- Introduction to DSI Studio (reconstruction, fiber tracking).

- Diffusion MRI quality control:

<iframe width="896" height="504" src="https://www.youtube.com/embed/stL4GMeTC1I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Assignment :

### task 1: Process dMRI files

1. Download subject (A00008326)'s dwi data from https://openneuro.org/datasets/ds001021/versions/1.0.0 (under SES-DS2), including *.nii.gz and .bval and .bvec.

2. [Generate SRC file](http://dsi-studio.labsolver.org/doc/gui_t1.html) and check if there are artifacts [(youtube)](https://www.youtube.com/embed/stL4GMeTC1I).

3. [Reconstruct the SRC file using DTI and GQI](http://dsi-studio.labsolver.org/doc/gui_t2.html).

### task 2: Automated fiber tracking

3. Run [automatic fiber tracking](http://dsi-studio.labsolver.org/doc/gui_t3_atk.html) on left arcuate fasciculus and compare it with manual result (on DTI and GQI fib files).

4. Compare their differences in FA/QA map and tractogram (on DTI and GQI fib files).

