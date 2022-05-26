# Differential Tractography

## Before practicum on Friday, please complete following:

### Review Paper

- Read through [Differential Tractography](https://github.com/frankyeh/Practicum/blob/gh-pages/Materials/paper/dT.pdf).

### Differential tractography tutorial

- [Documentation.](https://dsi-studio.labsolver.org/doc/gui_t3_dt.html)

- Tutorial video:
<iframe width="600" height="300" src="https://www.youtube.com/embed/EWOGQ3QTrnw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---


## During practicum on Friday:

### Diffusion MRI analysis methods

![image](https://user-images.githubusercontent.com/275569/170546285-d395bf1c-2eaf-4840-81b7-bd81c4aa53bb.png)


### Differential tractography demonstration

<img src="https://user-images.githubusercontent.com/275569/170547111-2def629f-c5b2-4127-93b8-303dfbcf2ae3.png" width=600>

### Flowchart

<img src="https://user-images.githubusercontent.com/275569/170546907-eb6763b7-d36c-4b00-9d20-49571dcd874b.png" width=600>


### Testing the Results

<img src="https://user-images.githubusercontent.com/275569/170547010-76a8ab42-0463-42eb-acab-4424b150beac.png" width=600>


---

### Practicum task 1: Differential tractography comparing subject data to a template: 

1. Download als05.gqi.1.25.fib.gz, from [ALS](https://drive.google.com/drive/folders/1q7YdmjaR-8w-pBUYe0nENnm3fiGnP1Md?usp=sharing).

2. Healthy subjects averaged [NQA map](https://zenodo.org/record/6324701/files/Grid258_nqa.nii.gz?download=1) and [FA map](https://zenodo.org/record/6324701/files/Grid258_dti_fa.nii.gz?download=1)

3. Follow the instruction video to get differential tractography. 

4. Adjust minimum length and differential tracking threshold to observe how they change the results.

### Practicum task 2: Differential tractography on longitudinal data: 

1. Download subject files at [TBI](https://drive.google.com/drive/folders/1Dj59qTblO96Q2xDKaEjtsghMuT8FYE54).

2. Convert and reconstruct base.nii.gz and follow.nii.gz to fib files (using QSDR to register baseline and follow-up scan in the same MNI space).

3. Follow the instruction video to get differential tractography. 

4. Adjust minimum length and differential tracking threshold to observe how they change the results.
