# Deep learning classification from brain MRI: Application to Alzheimer's disease

Numerous deep learning approaches have been proposed to classify neurological
diseases, such as Alzheimer’s disease (AD), based on brain imaging data.
However, classification performance is difficult to compare across studies due
to variations in components such as participant selection, image preprocessing
or validation procedure. Moreover, these studies are hardly reproducible because
their frameworks are usually not publicly accessible and because implementation
details are lacking. Lastly, some of these works may report a biased performance
due to inadequate or unclear validation or model selection procedures.
In a recently published article [[Wen et al. 2020](https://doi.org/10.1016/j.media.2020.101694)],
we aimed to address these limitations by proposing an open-source framework
for AD classification using convolutional neural networks and structural MRI.
The framework comprises tools to automatically convert publicly available
AD datasets into the BIDS standard, and a modular set of image preprocessing procedures,
classification architectures and evaluation procedures dedicated to deep learning.
The proposed framework can be used to provide a baseline performance against which
new methods can easily be compared. Researchers working on novel methods can easily
replace a given part of the pipeline with their own solution (e.g. a classifier
with a new architecture), and evaluate the added value of this specific new component
over the baseline approach provided. All the code of the framework and the experiments
is publicly available: general-purpose tools have been integrated into the
Clinica software (www.clinica.run) and the paper-specific code is available at:
https://github.com/aramis-lab/AD-DL.


This tutorial will guide you through the steps necessary to carry out an analysis
aiming to differentiate patients with Alzheimer's disease from healthy controls
using structural MR images and convolutional neural networks. It will particularly
highlight traps to avoid when carrying out this type of analysis.
The tutorial will rely on [Clinica](http://www.clinica.run), a software platform
for clinical neuroimaging studies, and [clinicadl](https://github.com/aramis-lab/ad-dl),
a tool dedicated to the deep learning-based classification of AD using structural MRI.
Even though we will focus on Alzheimer's disease, the principles explained are
general enough to be applicable to the analysis of other neurological diseases.

The Jupyter Book is divided into the following sections:

- [Clinical context: Alzheimer's disease](Notebooks-AD-DL/dataset).

- [Prepare your neuroimaging data](Notebooks-AD-DL/preprocessing).

- [Classify T1 MRI using precomputed CNN models and **clinicadl**](Notebooks-AD-DL/inference).

- [Defining the labels and validation procedures for classification](Notebooks-AD-DL/label_extraction).

- [Train your own CNN models (optional)](Notebooks-AD-DL/training).


## Execution of the notebooks

Each of these sections can be downloaded as a notebook (a mix of text and code)
that can be executed locally in your computer or run in a
"cloud" instance (useful if you do not have a GPU available in your computer).
In the later case, links to instances of Google Colab are displayed.

### Local execution of the notebooks

The local environment to execute the notebooks can be installed using
miniconda. Please follow instructions
[here](https://docs.conda.io/en/latest/miniconda.html) to install it.

Once Conda is installed, create an environment with all the dependencies.
*Warning*: It is strongly recommended to use a computer with at least one GPU
card, especially if you want to train your own model.

For the preprocessing stage, you must install this software previously:
[ANTs](http://stnava.github.io/ANTs/).

The Python's required libraries are :

- PyTorch
- Clinica
- Clinicadl
- jupyter-notebook
