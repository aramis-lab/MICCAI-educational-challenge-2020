# T1 MRI Classification using Deep Learning

This tutorial will show necessary steps to run succesfully image classificaiton
of T1 MRI using [Clinica](http://www.clinica.run) and
[clinicadl](https://github.com/aramis-lab/ad-dl).

This Jupyter Book is divided in five sections:

- Getting the database and short description.

- Preprocessing the data with the `clinica T1_Linear` pipeline.

- Prepare T1 MRI images for Deep Learning models.

- Classify T1 MRI  using precomputed CNN models and **clinicadl**.

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

The Python required library are :

- pytorch
- clinica
- clinicadl
- jupyter-notebook


