# MICCAI-educational-challenge-2020

This repository contains the supports for a tutorial to perform **AD
Classification using Clinica**.

When cloning remember to include the submodules:
```
git submodule update --init --recursive
```

Jupyter-book is automatically deployed here:
https://aramislab.paris.inria.fr/clinicadl/tuto/intro.html


When [Notebooks-AD-DL](https://github.com/aramis-lab/Notebooks-AD-DL) is
updated, type:
```
git submodule update --remote
```
to update the Jupyter-book.

To run locally, please install the necessary packages inside a conda environment:

```bash
conda create -y -n clinicadl_tuto python=3.7
conda activate clinicadl_tuto
pip install jupyterlab
pip install clinicadl==0.1.2
```

Then, you can clone the repository containing this tutorial and lauch the
notebooks from inside:

```bash 
git clone git@github.com:aramis-lab/MICCAI-educational-challenge-2020.git
cd ./Notebooks-AD-DL
jupyter notebook
```
