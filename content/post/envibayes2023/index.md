---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Envibayes2023"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2023-10-27T08:57:42-04:00
lastmod: 2023-10-27T08:57:42-04:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---



This is a recap of the [Envibayes Workshop on Complex Environmental Data](https://statistics.colostate.edu/envibayes-workshop/).

The purpose of this recap is to consolidate notes, with a focus on ideas I think might have potential for personal research pursuits.

The recap is ordered by talk, though some notes are only tangentially related to the talk under which they appear. 


## Veronica Berrocal *Stationarity or non-stationarity: that is the question*

- Mark Risser's [work](https://sites.google.com/site/markdrisser/research), especially on [non-stationary GP kernals for massive datasets](https://www.nature.com/articles/s41598-023-30062-8)
- four broad methods of nonstationary GP's 
   1. covariates in covariance matrix
   2. covariate-informed local partitioning
   3. identification of local stationarity regions
   4. new class of prior (eg. [CUSP-MRA prior](10.1111/biom.13446))
- joint Bayesian data fusion - eg. Nonstationary spatiotemporal Bayesian data fusion for pollutants in the near-road environment ([Gilana 2019](https://doi.org/10.1002/env.2581))
- regression-based Bayesian data fusion - eg. Model evaluation and spatial interpolation by Bayesian combination of observations with outputs from numerical models ([Fuentes 2005 ](https://doi.org/10.1111/j.0006-341X.2005.030821.x))
- covariate-driven segmentation - eg. Nonstationary spatial prediction of soil organic carbon: Implications for stock assessment decision making  ([Risser 2019](https://doi.org/10.1214/18-AOAS1204))

- fast approximation methods for fully Bayesian ensembles of different spatial prediction methods
    - Identifying regions of inhomogeneities in spatial processes via an M-RA and mixture priors ([Bededetti 2021](https://doi.org/10.1111/biom.13446))
    - Deep Gaussian Processes - [Damianou 2013](https://proceedings.mlr.press/v31/damianou13a.html), [Neil Lawrence talk](https://inverseprobability.com/talks/notes/deep-gaussian-processes-a-motivation-and-introduction.html), [survey](https://doi.org/10.48550/arXiv.2106.12135)

## Andee Kaplan *Improving Bayesian inference for streaming data*

- Making Recursive Bayesian Inference Accessible ([Hooten 2021](https://doi.org/10.1080/00031305.2019.1665584))
- Generative Filtering for Recursive Bayesian Inference with Streaming Data ([Taylor 2023](https://arxiv.org/pdf/2309.14271.pdf)
- Sequential Markov Chain Monte Carlo ([Yang 2013](https://doi.org/10.48550/arXiv.1308.3861)

## Maryclare Griffin *Log-Gaussian Cox Process Modeling of Large Spatial Lightning Data using Spectral and Laplace Approximations*

- Vecchia-Laplace approximations of generalized Gaussian processes for big non-Gaussian spatial data ([Zilber 2019](https://arxiv.org/abs/1906.07828))

- Circular embeddings are highly efficient

## Student Papers

- A dynamic spatial filtering approach to mitigate underestimation bias in field calibrated low-cost sensor air-pollution data ([Heffernan](https://doi.org/10.48550/arXiv.2203.14775))
    -pm2.5 downscaler inverse regression
- Dynamic Population Models with Temporal Preferential Sampling to Infer Phenology ([Schwob 2022](https://doi.org/10.48550/arXiv.2212.05180)
- New spatial models for integrating standardized detection-nondetection and opportunistic presence-only data: application to estimating risk factors associated to powerline-induced death of birds [Sicacha-Parada 2023](https://doi.org/10.48550/arXiv.2303.02088)


## Amy Herring *Low Rank Longitudinal Factor Regression*

- connections to brain imaging?


## Henry Scharf *Predicting fine-scale taxonomic variation in landscape vegetation using large satellite imagery data sets*

- arxiv [here](https://doi.org/10.48550/arXiv.2309.10325)


## Maggie Johnson *Tracking plant stress from space: Improving estimates of evapotranspiration through spatiotemporal data fusion*

- Multisensor Fusion of Remotely Sensed Vegetation Indices Using Space-Time Dynamic Linear Models ([Johnson 2021](https://doi.org/10.1111/rssc.12495))

## Yawen Guan *A Bayesian Hierarchical Approach for Modeling Tree Cover Change*

- Dynamic spatio-temporal models for spatial data [Hefley 2017] (https://doi.org/10.1016/j.spasta.2017.02.005)

## Cory Zigler *Bayesian Causal Inference with Uncertain Physical Process Interference*

- Solving the SPDE - A Mechanistic Model of Annual Sulfate Concentrations in the United States ([Wikle 2022](10.1080/01621459.2022.2027774))

## Amy Braverman *Statistical Challenges for the Next Generation of NASA’s Earth Observing Satellites*

- Post hoc Uncertainty Quantification for Remote Sensing Observing Systems [Braverman 2021](https://dus.jpl.nasa.gov/Papers/2021.BravermanEtAl.JUQ.pdf)
- how to preserve local information on a global scale? 

## Robert Gramacy *Contour Location for Reliability in Airfoil Simulation Experiments using Deep Gaussian Processes*

- precursor: Bayesian inference for non-stationary spatial covariance structure via spatial deformations [Schmidt 2003](https://doi.org/10.1111/1467-9868.00413)
- layers of Gaussians: Elliptical slice sampling [Murray 2010](https://proceedings.mlr.press/v9/murray10a.html)
- Vechia approx: Vecchia-Approximated Deep Gaussian Processes for Computer Experiments [Sauer 2022](https://doi.org/10.1080/10618600.2022.2129662)

## Abhirup Datta *Combining machine learning with Gaussian processes for geospatial data*

- machine learning for nonlinear geospatial analysis
    1. residual kriggin (Olsen 2020)
    2. adding spatial covariates (Wang 2019)
    3. Embed ML in spatial GLMM (this is best)

 - Random Forests for Spatially Dependent Data [Saha 2021](https://doi.org/10.1080/01621459.2021.1950003)

- IDEA: uncertainty quantification for graphical neural nets, get CI's for mean, stoch gradient MCMC


## Matt Koslovsky *A Bayesian model for measurement error in multinomial data*
- zero inflated dirichlet model
- data augmentation: normalized random measures
- Bayesian Inference for Logistic Models Using Pólya–Gamma Latent Variables ([Polson 2013](https://doi.org/10.1080/01621459.2013.829001)
- A Bayesian zero-inflated Dirichlet-multinomial regression model for multivariate compositional count data ([Koslovsky 2023](https://doi.org/10.1111/biom.13853))

## Alexandra Schmidt *Temporal misalignment in geostatistical*

- spatiotemporal methods in env. epi

## Ephraim Hanks *A Mixture of OU-processes Framework for Jointly Modeling Animal Movement and Species Distribution Data*

- Adaptive MCMC ([Shaby 2010](https://m-clark.github.io/docs/ld_mcmc/index_onepage.html)

## Toryn Schafer *Inverse reinforcement learning for animal behavior in the environment*

- RL <--> ABM <--> LMDP: Bayesian inverse reinforcement learning for collective animal movement [Schafer](https://mhooten.github.io/publications/Schafer_etal_AOAS_2022.pdf)


## Other 

- Calibration identifiability issue - Bayesian calibration of computer models ([Kennedy 2002](https://doi.org/10.1111/1467-9868.00294))
- [Dunson](https://scholar.google.co.uk/citations?user=KwEOawwAAAAJ&hl=en)

