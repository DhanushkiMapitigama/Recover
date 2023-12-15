# Machine Learning Driven Candidate Compound Generation for Drug Repurposing
Based on RECOVER: sequential model optimization platform for combination drug repurposing identifies novel synergistic compounds *in vitro*
[![DOI](https://zenodo.org/badge/320327566.svg)](https://zenodo.org/badge/latestdoi/320327566)

This repository is an implementation of RECOVER, a platform that can guide wet lab experiments to quickly discover synergistic drug combinations,
([preprint](https://arxiv.org/abs/2202.04202)), howerver instead of using an ensemble model to get Synergy predictions with uncertainty, we used multiple realization of a Bayesian Neural Network model. 
Since the weights are drawn from a distribution, they differ for every run of a trained model and hence give different results. The goal was to get a more precise uncertainty and achieve i quicker since the model doesn't have to be trained multiple times. 

<p float="left">
  <img src="docs/images/ProjectInfographics.png" alt="Overview" width="300"/>
  <img src="docs/images/ModelOverview.png" alt="Model Overview" width="400"/>
</p>

## Repository overview
There are 6 branches in this Git Repository.

**Master**, where the original RECOVER is stored with Bayesian setup but original config files, so the initial pipeline can be easily recreated.   
**Bayesian_after_merge**, with a Bayesian model used only in the layers after the bilinear merge.   
**Bayesian_before_and_after_merge**, with a Bayesian model used in the layers before and after the bilinear merge.  
**Weight_uncertainty**, a Bayesian Neural Network library implemented from scratch and two priors introduced in order to optimize the model. (https://doi.org/10.48550/arXiv.1505.05424)  

Every branch will be further explaned in its own README.

## Environment setup

**Requirements and Installation**: 
For all the requirements and installation steps check th orginal RECOVER repository (https://github.com/RECOVERcoalition/Recover.git). 

## Running the pipeline

Configuration files for our experiments are provided in the following directory: `Recover/recover/config`

To run the pipeline with a custom configuration:
- Create your configuration file and move it to `Recover/recover/config/`
- Run `python train.py --config <my_configuration_file>`

For example, to run the pipeline with configuration from 
the file `model_evaluation.py`, run `python train.py --config model_evaluation`.

Log files will automatically be created to save the results of the experiments.
