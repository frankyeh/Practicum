# Week 6 Correlational Tractography

Linggang Luo

*Feb 26th 2022*

Some materials will be shared via our [google drive folder](https://drive.google.com/drive/folders/12XGKtBVUb7i-uW_LSkMERFRhP7S95OrQ?usp=sharing) for confidentiality reasons.


---


## Before practicum on Friday, please complete following:

### Review Paper

- Skim through [Connectometry](Materials/paper/connectometry.pdf).

### Correlational tractography tutorial

- [Documentation.](https://dsi-studio.labsolver.org/doc/gui_cx.html)

- Tutorial video:
<iframe width="896" height="504" src="https://www.youtube.com/embed/qC8jx6XZHGI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---


## During practicum on Friday:

- Dr. Yeh's Q&A.

#### Correlational tractography demonstration


---

### Practicum task 1: white matter tract correlated with BMI

1. Download cmu60.db.fib.gz and cmu60.csv.
2. Set permutation count to 500.
3. uncheck [FDR control] and run analysis using different T threshold (2 and 3).
4. check [FDR control] (< 0.05) and run analysis use different T threshold (2 and 3)to see how it affects results.

### Practicum task 2: Group stratified analysis 

1. Download cmu60.db.fib.gz and cmu60.csv.
2. Repeat 1 on male group.
3. Repeat 2 on female group.

### Practicum task 3: Post-hoc analysis

1. Use tractography results from task 1 to extract QA values from the connectometry DB file.
2. Plot scatter plot (BMI vs QA).
