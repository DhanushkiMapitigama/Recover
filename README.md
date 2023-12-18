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

## Bayesian_after_merge
The model with Bayesian layers used only in the layers after the bilinear merge. Below implementations and experiments are done within the work in this branch (All the work can be recreated using the code in master, use the config files to define model setup and the required experiments.)
- Conversion of the model to Bayesian NN using the torch BNN library. Improve training implementation to support the optimization with MSE + KL divergence
- Test functions were adjusted to capture uncertainty by considering a given number of realizations
- Introdunction of new aquisition function/s
- Basic training and Active Learning with the bayesian model
- Introduced Scaled sigmoid and experiments done with and without the scaled sigmoid
- Experiments done to verify the correctness of results for permuted combinations
- Expermentations done to check the robustness of the model for different noise (gaussian, random, salt pepper)

## Running the pipeline

Configuration files for our experiments are provided in the following directory: `Recover/recover/config`

To run the pipeline with a custom configuration:
- Create your configuration file and move it to `Recover/recover/config/`
- Run `python train.py --config <my_configuration_file>`

For example, to run the pipeline with configuration from 
the file `model_evaluation.py`, run `python train.py --config model_evaluation`.

Log files will automatically be created to save the results of the experiments.
