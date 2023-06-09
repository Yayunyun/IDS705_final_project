### IDS705 final project
# De-biasing a Gender-Biased Chest X-ray Classification Model
This repository if for the final project for Duke 2023 Spring IDS 705 final project. This project is done collaboratively by *Ya-Yun Huang, John, Aditya Emmanuel Arokiaraj, Van Meter, Kristi Ann and Wang, Zhonglin*.

This project aims to **detect underdiagnosis bias for under-served peopole, such as female, black and low socio-economic status, in the CNN model that is trained on the dataset where these people are under-represented**. We mainly focus on the underdiagnosis bias for female in the CNN model used for CXR binary task classifiaction(with clinical finiding and without). 

The main goal of this dataset includes 2 section:
1. Introduce gender bias to the model and detect the bias with the fairness metric we defined.
2. Incoportate a custom loss function that take the fairness metric as a penalty term to de-bias the model.

We have 2 training/validation sets as shown in the following figure:
- Sick-male: Sick-female = 50:50
- Sick-male:Sick-females = 80:20
The number of non-sick males, non-sick females and sick-males are the same.
<img width="534" alt="Screen Shot 2023-04-15 at 7 23 46 PM" src="https://user-images.githubusercontent.com/110958060/233205323-3fd68f8a-eaa2-4b87-aed6-cdb2b9248473.png">

We have 3 testing set with sick-male:sick female = 50:50, 70:30 and 90:10. The number of non-sick males, non-sick females and sick-males are the same.

Eventually we would have 3 model:
- Unbiased model: train on the 50:50 training set with normal binary cross entropy loss function
- Biased model: train on the 80:20 training set with normal binary cross entropy loss function
- De-Biased model: train on the 80:20 training set with fair loss function which takes the following form:
<img width="615" alt="Screen Shot 2023-04-18 at 11 38 45 PM" src="https://user-images.githubusercontent.com/110958060/233206057-6b2d1ba1-3cd6-490a-a917-683456987685.png">


## Files description
- `EDA_preprocessing.ipynb`: Exploratory analysis of the orignial dataset and the code for producing the dataset we used for modeling and testing
- `training_testing_biased.ipynb`: Training and testing code for the biased model.
- `training_testing_unbiased.ipynb`: Training and testing code for the unbiased model.
- `training_testing_debiased.ipynb`: Training and testing code for the de-biased model.
- `requirements.txt`: All dependencies required to install to run the code in this repository.

## Data
We utilize the [**National Institute of Health Chest X-Ray dataset made publically available on Kaggle in 2018**](https://www.kaggle.com/datasets/nih-chest-xrays/data). This dataset include 2 parts: one includes all of the 112,120 CXR images and one is a `.csv` file that includes information for each CXR images. Due to limited computational resources, we were not able to conduct this project with all of the images and to upload those images to these github repo. Therefore, for our experiment we uploaded each folder of image data(`image`, `image2` to `image12`) and the information csv file `Data_Entry_2017.csv` to google drive and use google colab to accesss these files in google drive. 

All of the data used in this project can be found in the Kaggle link provided above. The pre-processing code is used to get the final subset of data used for this project can be found in the file `EDA_preprocessing.ipynb`.

## Training and testing
To run the code in `training_testing_biased.ipynb`, `training_testing_unbiased.ipynb`, and `training_testing_debiased.ipynb`, the user has to finish the steps in `EDA_preprocessing.ipynb` to get the needed data. After getting those data, user just need to run the jupyter notebook step by step to reproduce the result.   
The only thing need to pay attention is the file path of the data. Since for this project, we use our personal google drive to save files, so the file path listed in these notebooks maybe different if others want to run.
