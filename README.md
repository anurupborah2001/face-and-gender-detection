# Face and Gender Detection

### Training flow process :

<img width="1152" height="307" alt="image" src="https://github.com/user-attachments/assets/2c76d830-58c6-4d7c-82d0-79e919fab974" />


### Data Preprocessing

1. Detect Faces
  a. Read Image and convert to RGB
  b. Appying Haar Cascade Classifier to get the co-ordinates of face
  c. Resize and crop face using coordinates from cascade classifier
  d. Label the images

# Exploratory Data Analysis
1. Distribution of Male and Female
 - Bar Chart
 - Pie Chart
2. What Distribution of size of all Images
 - Histogram
 - Box Plot
 - Split by “Gender”
3. Make the decision of width & height to resize using above chart.
4. Remove the few images that are having very less size

# Feature Extraction
1. Using the save data model, create Eigen face
[Eigen faces Research paper](https://sites.cs.ucsb.edu/~mturk/Papers/mturk-CVPR91.pdf)
2. Finding the right number of components for Principal Component Analysis(PCA)
3. Using Principal Component Analysis(PCA) to extract the features of the face
4. Visualize the Eigen face of sample image

# Training the model
1. Load the PCA model generated
2. Split the dataset into 80%(train set) and 20%(test set)
3. Train the model using Support Vector Machine.
4. Using GridSearchCV to evaluate the best parameter while training the model to be used for prediction

# Model Evaluation
- Classification Report
  - Precision, Recall, F1-Score

- Kappa Score
  - -ve (worst model)
  - 0 to 0.5 (bad model)
  - 0.5 to 0.7 (Good Model)
  - 0.7 to 0.9 (Excellent Model)
  - 0.9 to 1.0 (Perfect Model)

- Area Under Curve(AUC)
  - Less than 0.5 (Worst Model)
  - 0.5 to 0.6 (Bad Model)
  - 0.6 to 0.8 (Good Model)
  - 0.8 to 0.9 (Excellent Model)
  - 0.9 to 1.0 (Perfect Model)

Generate graph to evaluate the Gamma, Co-efficient, Kernel

# Prediction
1. **Image Prediction:** Using a sample image, to detect the face and classify the gender.
2. **Real Time Prediction:** Real-time video to detect the face and classify the gender.


**NB:** Please note that the model files are not avaialble so in order to run need to train the model.

## Deploy the model to Heroku

The deploy files will be in `deploy_app` folder

The below are the steps to perform to deploy to Heroku:

1. Deploying the app to heroku needs a library dependency named `gunicorn`. We need to run the below command to download the library:

```bash
!pip install gunicorn
```

2. Create a Proc file , which the Heroku app needs it

```bash
web: gunicorn main:app
```

Actually we cannot directly deploy any application that has dependency on OpenCV and these dependencies also need to be installed in the cloud server.For this we need to create another file names `Appfile` and inside this file we need to specify the kernel libraries that needed to be installed in the kernel binaries.

The `Appfile` will contain the below libraries:

```bash
libsm6
libxrender1
libfontconfig1
libice6
```
