# Deep_Learning_Predicts_Dysbiosis
Deep Learning of Human Gut Microbiome Images: A General Dysbiosis Prediction Model

## Summary
Short-read WGS sequence data derived from human stool samples, totalling 17,000+ samples and 45 phenotypes, was downloaded from pubic repositories and profiled with the [MetaTax pipeline](https://github.com/mjnetherland19/MetaTax). Healthy and non-healthy metadata was curated manually, and the taxonomic profiles for each cohort were transformed and batch corrected. Separately, each cohort's correlation matrix was sent for dimensional reduction by Uniform Manifold Approximation and Projection (UMAP) and hierarchical clustering, to find clusters of taxa. Clusters are used for color filling and the Jonker-Volgenant (J-V) algorithm is used to map the UMAP coordinates to an ordered grid. Using this mapping, individual sample images are constructed with each pixel location corresponding to the presence of a taxon and its color corresponding to its cluster membership. A CNN was constructed according to the GoogLeNet architecture and trained on those images for binary healthy/non-healthy prediction. The inspiration for this image building pipeline and model architecture was inspired by Shen, Wan Xiang, et al. and their MEGMA model [1]. My model differs from theirs in that I use presence/absence instead of relative abundance for pixel intensity, the greater number of samples used for training, and the interpretation of the salience maps to identify phenotype correlated taxa, as this was not detailed in their publication.

## Dataset Summary
| Phenotype        | # of samples            | Phenotype        | # of samples            |
|:-------------:|:-------------------------:|:-------------:|:-------------------------:|
Healthy | 11889  | Colorectal polyps | 30
Ulcerative Colitis | 434 | Salmonellosis | 29
Crohn's disease | 374 | Cancer | 27
Colorectal cancer | 352 | Autistic Spectrum Disorder | 25
T2D | 232 | Asthma | 24
ACVD | 228 | Behcet's disease | 24
Ankylosing spondylitis | 191 | Vibrio cholerae infection | 21
Overweight | 178 | Campylobacteriosis | 21
Liver cirrhosis | 158 | Kidney Disease | 21
Adenoma | 140 | Cystic fibrosis | 19
Lung Disease | 134 | IBD | 10
Thyroid | 96 | Hypertension | 9
Rheumatoid arthritis | 92 | Fungal overgrowth | 7
Schizophrenia | 65 | Liver Disease | 5
IGT | 49 | Hypercholesterolemia | 5
Obesity | 47 | Shigellosis | 4
Carcinoma | 46 | HIV | 3
Cancer treatment | 40 | Escherichia gastroenteritis | 3
IBS | 38 | Osteoporosis | 2
Migraine | 36 | Metastases | 1
Underweight | 33 | Sibo | 1
Neutropenia | 33 | Multiple phenotypes | 39
Autoimmune | 31

## Microbiome Image and Saliencey Map
The saliencey map is a way of opening the black box of deep learning models. It provides an explanation of how the model made its predictions. In this case, a heatmap of the importance of each pixel (taxon) to the accuracy of classification.

<img width="969" height="502" alt="image" src="https://github.com/user-attachments/assets/233b5d03-cb27-4db5-8ad1-27890b7b1fc0" />


## References
[1] Shen, W. X., Liang, S. R., Jiang, Y. Y., & Chen, Y. Z. (2023). Enhanced metagenomic deep learning for disease prediction and consistent signature recognition by restructured microbiome 2D representations. Patterns, 4(1).
