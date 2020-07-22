# MRI Classification

This tutorial explains the  necessary steps to succesfully run automatic T1 MRI
classification of T1 MRI using [Clinica](http://www.clinica.run) and
[clinicadl](https://github.com/aramis-lab/ad-dl).

To achieve this, the present Jupyter Book is divided into the following sections:

- [Description of dementia study context](Notebooks-AD-DL/dataset).

- [Prepare raw neuroimaging datasets for Deep Learning models](Notebooks-AD-DL/preprocessing).

- [Classify T1 MRI using precomputed CNN models and **clinicadl**](Notebooks-AD-DL/inference).

- [Defining the labels and validation procedures for classification](Notebooks-AD-DL/label_extraction).

- [Train your own CNN models (optional)](Notebooks-AD-DL/training).

Each of these sections can be download as a notebook (a mix of text and code)
that can be executed locally in your computer or it can be run in a
"cloud" instance (e.g. you don't have a GPU available in your computer).
In the former case, links to instances of Google Colab are displayed.

If you want to test the local version of the notebooks, please verify that
you have installed the correct notebook environment.

## Local execution of the notebooks

Use Conda/miniconda to setup your local environment and to execute these
notebooks. If the tool is not installed in your system, please follow [these
instructions](https://docs.conda.io/en/latest/miniconda.html) to install it.

```warning
It's strongly recommended to use a computer with at least one GPU
card, specially it you want to train your own model.
```

Once Conda is installed, a good pratice consist in create a new environment from
raw and install inside `clinicadl` and of course `jupyter notebook`:

```bash
conda create -y -n clinicadl_tuto python=3.7
conda activate clinicadl_tuto
pip install numpy==1.17 jupyterlab
pip install clinicadl=0.0.2b2
```

Then, you can clone the repository containing this tutorial and lauch the notebooks from inside:

``` 
git clone git@github.com:aramis-lab/MICCAI-educational-challenge-2020.git
cd ./Notebooks-AD-DL
jupyter notebook
```
