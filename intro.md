# MRI Classification

This tutorial shows the  necessary steps to succesfully run automatic T1 MRI
classification of T1 MRI using [Clinica](http://www.clinica.run) and
[clinicadl](https://github.com/aramis-lab/ad-dl).

To achieve this, this Jupyter Book is divided into the following sections:

- Generating a test database.

- Preprocessing the data with the `clinica T1_Linear` pipeline.

- Prepare T1 MRI images for Deep Learning models.

- Classify T1 MRI using precomputed CNN models and **clinicadl**.

- Train your own CNN models (optional).

Each of these sections can be download as a notebook (a mix of text and code)
that can be executed locally in your computer or that can be launched  in a
"cloud" instance (e.g. you don't have a GPU available in your computer).

If you want to test the local version of the notebooks, please verify that 
you have installed the correct notebook environment

## Local execution of the notebooks

The local environment to execute the notebooks can be installed using
miniconda. Please follow instructions
[here](https://docs.conda.io/en/latest/miniconda.html) to install this tool.

Once Conda is installed, create an environment with all the dependencies.
*Warning*: It's strongly recommended to use a computer with at least one GPU
card, specially it you want to train your own model. 

For the preprocessing stage, you must install this software previously:
[ANTs](http://stnava.github.io/ANTs/).

The Python's required libraries are :

- pytorch
- clinica
- clinicadl
- jupyter-notebook


