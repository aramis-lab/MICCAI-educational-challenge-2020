# Deep learning classification from brain MRI: Application to Alzheimer's disease

## Introduction

Numerous deep learning approaches have been proposed to classify neurological
diseases, such as Alzheimer’s disease (AD), based on brain imaging data.
However, classification performance is difficult to compare across studies due
to variations in components such as participant selection, image preprocessing
or validation procedure. Moreover, these studies are hardly reproducible
because their frameworks are usually not publicly accessible and because
implementation details are lacking. Lastly, some of these works may report a
biased performance due to inadequate or unclear validation or model selection
procedures.  In a recently published article ([Wen et al.
2020](https://doi.org/10.1016/j.media.2020.101694)), we aimed to address these
limitations by proposing an open-source framework for AD classification using
convolutional neural networks and structural MRI.

The ClinicaDL framework comprises tools to automatically convert publicly
available AD datasets into the BIDS standard, and a modular set of image
preprocessing procedures, classification architectures and evaluation procedures
dedicated to deep learning. This framework can be used to provide a baseline
performance against which new methods can easily be compared. Researchers working
on novel methods can easily replace a given part of the pipeline with their own
solution (e.g. a classifier with a new architecture), and evaluate the added
value of this specific new component over the baseline approach provided.
The code of the framework is publicly available: general-purpose tools have
been integrated into the Clinica software [^mynote]
and the framework-specific code is available at:
[https://github.com/aramis-lab/AD-DL](https://github.com/aramis-lab/AD-DL).

[^mynote]: [www.clinica.run](http://www.clinica.run)

This tutorial will guide you through the steps necessary to carry out an
analysis aiming to differentiate patients with Alzheimer's disease from healthy
controls using structural MR images and convolutional neural networks. It will
particularly highlight traps to avoid when carrying out this type of analysis.
The tutorial will rely on [Clinica](http://www.clinica.run), a software
platform for clinical neuroimaging studies, and
[ClinicaDL](https://github.com/aramis-lab/ad-dl), a tool dedicated to the deep
learning-based classification of AD using structural MRI. Even though we will
focus on Alzheimer's disease, the principles explained are general enough to be
applicable to the analysis of other neurological diseases.

The Jupyter Book is divided into the following sections:

- Background

  - [Clinical context: Alzheimer's disease](Notebooks-AD-DL/dataset)

  - [Deep learning classification](Notebooks-AD-DL/deep_learning)

- The basics

  - [Prepare your neuroimaging data](Notebooks-AD-DL/preprocessing)

  - [Perfom classification using pretrained models](Notebooks-AD-DL/inference)

- Going further

  - [Define your population](Notebooks-AD-DL/label_extraction)

  - [Train your own models](Notebooks-AD-DL/training)


## Execution of the notebooks

Each of these sections can be downloaded as a notebook (a mix of text and code)
that can be executed locally in your computer or run in a
"cloud" instance (useful if you do not have a GPU available in your computer).
In the later case, links to instances of Google Colab are displayed.

### Local execution of the notebooks

Use Conda/miniconda to setup your local environment and to execute these
notebooks. If the tool is not installed in your system, please follow [these
instructions](https://docs.conda.io/en/latest/miniconda.html) to install it.

```{warning}
It is strongly recommended to use a computer with at least one GPU
card, especially if you want to train your own model.
```

Once Conda is installed, a good practice consists in creating a new environment
and installing inside `clinicadl` and of course `jupyter notebook`:

````{admonition} Environment installation instructions
:class: dropdown, tip
```bash
conda create -y -n clinicadl_tuto python=3.7
conda activate clinicadl_tuto
pip install numpy==1.17 jupyterlab
pip install clinicadl=0.0.2b4
```
````

Then, you can clone the repository containing this tutorial and launch the
notebooks once inside the repository:


````{admonition} Cloning repository
:class: dropdown, tip
```bash
git clone git@github.com:aramis-lab/MICCAI-educational-challenge-2020.git
cd ./Notebooks-AD-DL
jupyter notebook
```
````

For the preprocessing stage, you must install this software: [ANTs](http://stnava.github.io/ANTs/).

### Running the notebooks in the Cloud

Some of the notebooks can be launched in a Google Colab instance, by clicking
on the icon in the upper side of the corresponding page. When launching the
instace an initial step is proposed to set-up the notebook with the necessary
software, this can take some time, particularly for the notebook "Prepare your
neuroimaging data". Notebooks can be run indepedently. 

## Troubleshooting

- If you are not able to exploit your GPU card, please reinstall Pytorch by
  following instructions available in their
  [webpage](https://pytorch.org/get-started/locally/).

- Some instructions of these notebooks need access to the Internet, in order to
  download templates, masks and models. Please verify that your internet
  connection is available.

- You need help? [Post an issue](https://github.com/aramis-lab/MICCAI-educational-challenge-2020/issues) in our repository!
