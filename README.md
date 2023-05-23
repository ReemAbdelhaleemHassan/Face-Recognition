<h1 align="center" id="title">Face Recognition Model</h1>

# Problem Statement
We intend to perform face recognition, face recognition means that for a given image you can tell the subject id. Our database of subject is very simple. It has 40 subjects and later it can be extended, below we will show the needed steps to achieve the goal of the model building.

# Procedures

### 1. Dataset Exploration  
- We downloaded the AT&T dataset from kaggle through that link [Download](https://www.kaggle.com/kasikrit/att-database-of-faces/)
- As we mentioned earlier that dataset was consisting of 40 different subject(person) and each person have 10 images with total 400 images
- Fortunately, the images have the same size 92x112 and it was accepted dimensions for our computation, besides the image was black and white so there is no RGB dimension consideration
### 2. Generate features space and label vector
- We will deal with the image(sample) as a flattened vector from the 2D matrix (converting 2D matrix to 1D vector) so the sample dimensions will be 92x122 = 10304
- so the total feature space will be 400(number of samples) and each image 10304 vector
- After stacking the images vector (400,10304), we have generated label vectors consisting of 40 different number from 1--> 40

### 3. Dataset Splitting
- perform dataset splitting using built-in function of scikit-learn with statifying that keep the data balanced as possible

### 4. Dimensionality Reductions using PCA
- As we mentioned earlier the sample has 10304 vector which is computational expensive and time consuming so we decide to apply principle componenet analysis on the dataset which reduce the dataset with some tolerence(alpha) from {0.8, 0.85, 0.9,0.95} and by definition the vector length is directly prop with the alpha
- We have recorded the results on the notebook with plotting R(sample vector length) vs Alpha and compare the results
- and by definition increasing the sample vector length increases the information gain and resultion of the dataset by the tradeoff is the compuational resources and time
### 4. LDA
- we have performed the LDA technique on the dataset the reduce the dimensionality and to solve the our classification problem

### 4. Simple classifer
- for the sack of simplicity we used the K-NN Classifer algorithm, after projecting our dataset on the PCA matrix one time, and on the LDA matrix another time we pass the projected samples to the classifer using knn scikit learn library to test and record the results

### 5. Classifer Tuning
- for knn classifer we have k hyperparamter to classify according to the nearest k sample classes in the feature space 
- {1,3,5,7} have used and record the accuracy everytime
