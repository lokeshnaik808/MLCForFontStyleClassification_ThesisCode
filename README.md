# Multi-Label Classification for Font Style Recognition

This repository contains one Jupyter Notebook (ThesisCodeLokeshNaik.ipynb) and various folders for different datasets and folders for saving the created models.
The folder structure should be created before running the provided code

Folder Structure and their descriptions are given below:
```
 - **/content/drive/MyDrive/Models** - Used to save the models.
 - **/content/drive/MyDrive/Thesis_data/v20** - Folder that has the training dataset for MCC or Combined Classifier.
 - **/content/drive/MyDrive/Thesis_data/v20_separated** - Folder that has the training dataset for Individual Classifiers.
 - **/content/drive/MyDrive/Thesis_data/Test_Images/** - Contains 2 full-page test images and respective JSON files with details of bounding boxes of each word in it. These are used to evaluate the models.
 - **/content/drive/MyDrive/Thesis_data/fonts** - Folder that contains the .ttf font files required for the data generator.
 - **/content/drive/MyDrive/Thesis_data/FUNSD/Benchmark_binarized** - Folder for the benchmark dataset created from the FUNSD dataset.
 - **/content/drive/MyDrive/Thesis_data/FUNSD/Benchmark_separated_single_classifier** - Folder for benchmark datasets for individual classifiers.
```

The notebook is organized into several sections, each described below:

* The first section covers the installation and import of the required libraries, as well as the connection to Google Drive.
* The second section loads TensorBoard and defines the `ReflectionPadding2D` class, which can be used as a custom layer in neural networks.
* The next two sections have code to create 4 individual binary classifiers for each label (OVL Approach) and a single Combined or MCC classifiers respectively. For each of the classifiers, there are 4 cells that need to be executed:
  1. Load Training Dataset for model, from folder `v20_separated` for separate classifiers and folder `v20` for MCC classifier
  2. Execute the TensorBoard callback code, which loads the classifier-specific benchmark dataset. The datasets are located in the `Benchmark_binarized` or `Benchmark_separated_single_classifier` folders for MCC and OVL or separate classifiers respectively.
  3. Model code with Feed-Forward architecture,
  4. Model code with Resnet Architecture.
Upon execution, cells 3 and 4:
  - Save the model after each epoch in the specified folder and name (if the named path does not exist, Google Drive creates them automatically).
  - Log the confusion matrix of the model's performance on the respective benchmark dataset in TensorBoard.

Note: The number of layers / channels / resnet blocks in code can be modified by adding or removing similar layer code as already present. There is an extra piece of code that can log confusion matrix of model performance independently of tensorboard.

* Subsequently, there is a section dedicated to testing the created and saved models on full-page form images. This section also evaluates the time required to perform classification on a full-page document.
* Then there is a section that includes the code used to generate training data and create datasets for each type of classifier (OVL or MCC).
* Finally. there are some sections that have optional code to perform analysis of Image Dimensions in Training and Benchmark Datasets and
Analysis by comparison of Layer Activations.

Ideally the cells should be executed sequentially as present in notebook

 
