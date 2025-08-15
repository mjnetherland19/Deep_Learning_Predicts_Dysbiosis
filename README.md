# Deep_Learning_Predicts_Dysbiosis
Deep Learning of Human Gut Microbiome Images: A General Dysbiosis Prediction Model

## Summary
Short-read shotgun sequence data derived from human stool samples, totalling 17,000+ samples and 45 phenotypes, was downloaded from pubic repositories and profiled with the MetaTax pipeline. Healthy and non-healthy metadata was curated manually, the taxonomic profiles for each cohort were transformed and batch corrected. Separately, each cohort's correlation matrix was sent for dimensional reduction by Uniform Manifold Approximation and Projection (UMAP) and hierarchical clustering, to find clusters of taxa. Clusters are used for color filling and the Jonker-Volgenant (J-V) algorithm is used to map the UMAP coordinates to an ordered grid. Using this mapping, individual sample images are constructed with each pixel location corresponding to the presence of a taxon and its color corresponding to its cluster membership. A CNN was constructed according to the GoogLeNet architecture and trained on those images for binary healthy/non-healthy prediction. The inspiration for this image building pipeline and model architecture was inspired by Shen, Wan Xiang, et al. and their MEGMA model [1]. My model differs from theirs in that I use simple presence/absence instead of relative abundance for pixel intensity, the greater number of samples used for training, and the interpretation of the salience maps to identify phenotype correlated taxa, as this was not detailed in their publication. There are a few other points that were not immediately apparent from their paper, which I will be sure to detail in the explanation of my methods.

## Dataset Summary




## References
[1] Shen, W. X., Liang, S. R., Jiang, Y. Y., & Chen, Y. Z. (2023). Enhanced metagenomic deep learning for disease prediction and consistent signature recognition by restructured microbiome 2D representations. Patterns, 4(1).
