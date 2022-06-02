# Correlational Tractography

## Before practicum on Friday, please complete following:

### Review Paper

- [Connectometry](Materials/paper/connectometry.pdf).

### Correlational tractography tutorial

- [Documentation.](https://dsi-studio.labsolver.org/doc/gui_cx.html)

- Tutorial video:
<iframe width="896" height="504" src="https://www.youtube.com/embed/qC8jx6XZHGI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---

## During practicum on Friday:

### Correlation tractography
<img src="https://user-images.githubusercontent.com/275569/171685414-3d6fb0d1-9c06-4fda-b9af-89684d29f2bf.png" width=700>

### Nonparametric tests

<img src="https://user-images.githubusercontent.com/275569/171685527-a5682d43-23ac-459a-97a4-b2006071f34f.png" width=500>


<img src="https://user-images.githubusercontent.com/275569/171685626-3df0097a-b19f-4180-851b-853e40e67d57.png" width=300>


### Hands-on: white matter tract correlated with BMI

1. Download [cmu60.db.fib.gz](https://zenodo.org/record/6324701/files/CMU60.db.fib.gz?download=1) and [cmu60.csv](https://zenodo.org/record/6324701/files/CMU60.demo.csv?download=1).
2. Set permutation count to 500.
3. uncheck [FDR control] and run analysis using different T threshold (2 and 3).
4. check [FDR control] (< 0.05) and run analysis use different T threshold (2 and 3)to see how it affects results.

### Hands-on: group stratified analysis 

1. Download cmu60.db.fib.gz and cmu60.csv.
2. Repeat 1 on male group.
3. Repeat 2 on female group.

### Hands-on: post-hoc analysis

1. Use tractography results from task 1 to extract QA values from the connectometry DB file.
2. Plot scatter plot (BMI vs QA).

---

## Assignment

