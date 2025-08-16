# Deep_Learning_Predicts_Dysbiosis
Deep Learning of Human Gut Microbiome Images: A General Dysbiosis Prediction Model

## Summary
1. Short-read WGS sequence data derived from human stool, totalling 17,000+ samples and 45 phenotypes, was downloaded from pubic repositories and profiled with the [MetaTax pipeline](https://github.com/mjnetherland19/MetaTax).
2. Healthy and non-healthy metadata was curated manually, and the taxonomic profiles for each cohort were transformed and batch corrected.
3. Separately, each cohort's correlation matrix was sent for dimensional reduction by Uniform Manifold Approximation and Projection (UMAP) and hierarchical clustering, to find clusters of taxa.
4. Clusters are used for color filling and the Jonker-Volgenant (J-V) algorithm is used to map the UMAP coordinates to an ordered grid.
5. Using only the Healthy coordinates, individual sample images are constructed, for either cohort, with each pixel location corresponding to the presence of a taxon and its color corresponding to its cohort-specific cluster membership.
6. A Convolutional Neural Network CNN was constructed according to the GoogLeNet architecture and trained on those images for binary healthy/non-healthy prediction.

The inspiration for this image building pipeline and model architecture was inspired by Shen, Wan Xiang, et al. and their MEGMA model [1]. My model differs from theirs in that I use presence/absence instead of relative abundance for pixel intensity, the greater number of samples used for training, and the interpretation of the salience maps to identify phenotype correlated taxa, as this was not detailed in their publication.

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

## Test Sets
The most exciting thing about this model is that it performs well on data it was not trained on. Here are the results of training on Multiple Sclerosis and Parkinson's datasets
<img width="812" height="514" alt="image" src="https://github.com/user-attachments/assets/fd9360bd-2568-4553-b4af-bad65f636b83" />

<img width="808" height="447" alt="image" src="https://github.com/user-attachments/assets/72d448bd-d063-423b-8755-2b7ee213718b" />

<img width="971" height="571" alt="image" src="https://github.com/user-attachments/assets/12780cd7-5479-4250-af91-f699f95f1df9" />


## Microbiome Image and Saliencey Map
The saliencey map is a way of opening the black box of deep learning models. It provides an explanation of how the model made its predictions, in the form of a heatmap of the importance of each pixel (taxon) to the accuracy of classification.

<img width="957" height="489" alt="image" src="https://github.com/user-attachments/assets/48d475f5-a828-4902-b1af-0690db212f37" />

<img width="954" height="510" alt="image" src="https://github.com/user-attachments/assets/9211baa8-9c67-4078-873f-3e24d738c72a" />




## References
[1] Shen, W. X., Liang, S. R., Jiang, Y. Y., & Chen, Y. Z. (2023). Enhanced metagenomic deep learning for disease prediction and consistent signature recognition by restructured microbiome 2D representations. Patterns, 4(1).
