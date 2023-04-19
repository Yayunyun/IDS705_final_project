### IDS705 final project
# De-biasing a Gender-Biased Chest X-ray Classification Model
This repository if for the final project for Duke 2023 Spring IDS 705 final project. This project is done collaboratively by Ya-Yun Huang, John, Aditya Emmanuel Arokiaraj, Van Meter, Kristi Ann and Wang, Zhonglin.

This project aims to detect underdiagnosis bias for under-served peopole, such as female, black and low socio-economic status, in the CNN model that is trained on the dataset where these people are under-represented. We mainly focus on the underdiagnosis bias for female in the CNN model used for CXR binary task classifiaction(with clinical finiding and without). 

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
- 
(a) contain a descriptive README.md file that explains what the repo is for, and how to use the code to reproduce your work (including how to set it up to run), (b) be well commented throughout all files, (c) list all dependencies in a requirements.txt file, (d) inform the user how to get the data and includes all preprocessing code, and (e) actually runs (i.e. we can successfully test it) and does what it says
