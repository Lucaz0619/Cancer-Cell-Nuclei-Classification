# Cancer-Cell-Nuclei-Classification
Identifying different types of cell nuclei in cancer samples using two different ConvNets

### Overview
This project uses deep learning models to classify different types of cells based on images of their nuclei, as part of the Deep Learning for MSC 2022-23 Kaggle competition at the University of Glasgow.
There are two types of models implemented: a custom Convolutional Neural Network (CNN) and a transfer learning approach using ResNet18.

### Dataset Description
Datasets are 100x100 pixel images with a cell nuclei in the centre of the following types which are shown below. 
However, there might be copyright concerns to share the data, so they are not included in the files.  

1. Normal epithelial cell nuclei with label 0.
2. Cancer epithelial cell nuclei with label 1.
3. Muscle cell nuclei with label 2.
4. Immune leukocyte cell nuclei with label 3.

#### File descriptions
- train.zip - zip file containing the training images
- test.zip - zip file containing the test images
- train.csv - csv file containing the training image filenams and ground truth labels (0, 1, 2, 3)
- example.csv - an example submission file in the correct format

#### Data fields
- Filename - filename of an image file.
- Label - the type of cell nucleus at the middle of the image.

#### Models
Two types of models were implemented for this project:  

- CNN: A custom Convolutional Neural Network was trained from scratch, including four convolutional layers, max pooling, and two fully connected layers.

- ResNet: A pre-trained ResNet18 model was fine-tuned using our training data. The first layer was adjusted to accept grayscale images, and the last fully connected layer was adjusted to classify four categories.

#### Hyperparameter Optimization
The Ray Tune library was used to perform hyperparameter optimization for the learning rate and batch size for both models.

#### Results
The models were evaluated based on their accuracy. The custom CNN model achieved an accuracy of 0.92063 on the Kaggle leaderboard, while the fine-tuned ResNet18 model achieved an accuracy of 0.97738.  

After training two models to classify cell nuclei images, Confusion Matrix and Captum's occlusion method were employed to generate attribute importance heatmaps. Resnet model demonstrates superior classification capabilities compared to CNN model, as indicated by the higher number of correct classifications.
On top of that, analyzing heatmaps helps identify potential areas for improvement, such as adjusting specific feature weightings or incorporating additional features. Overall, based on heatmap analysis, Resnet model appears to be better suited for this task.
