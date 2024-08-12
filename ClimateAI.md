## Climate Change AI - All Projects related to sustainability and Climate Change



## Project 1 - Land Usage and Land Coverage (LULC)

This project is derived from EuroSAT: A Novel Dataset and Deep Learning Benchmark for Land Use and Land Cover Classification [Paper Link](https://arxiv.org/abs/1709.00029)
and source of inspiration was this article [Article Link](https://www.wri.org/insights/7-things-know-about-ipccs-special-report-climate-change-and-land , Data set [dataset](https://github.com/phelber/EuroSAT)

## Problem Statement -Understanding Climate Impact by LULC

Land use change such as deforestation and land degradation are among the primary drivers of these emissions. Rapid urbanization leading to an increase in built-up areas as well as a massive loss of terrestrial carbon storage can also result in large carbon emissions.

Mapping the extent of land use and land cover categories over time is essential for better environmental monitoring, urban planning and nature protection. For example, monitoring changes in forest cover and identifying drivers of forest loss can be useful for forest conservation and restoration efforts. Assessing the vulnerability of certain land cover types, such as settlements and agricultural land, to certain risks can also be useful for for disaster risk reduction planning as well as long-term climate adaptation efforts.

With the increasing availability of earth observation data coupled with recent advanced in computer vision, AI & EO has paved the way for the potential to map land use and land cover at an unprecedented scale. In this tutorial, we will explore the use of Sentinel-2 satellite images and deep learning models in Pytorch to automate LULC mapping.

# Objective of the project 
Objective 

1. train a deep learning model for image classification using Pytorch
2. generate land use and land cover maps using Python GIS

Aim :To classify satellite images into 10 Land Use and Land Cover (LULC) categories using the EuroSAT dataset and a ResNet-50 CNN model.

## Project Flow 

STEP 1 DATA PREPARATION 


![image](https://github.com/user-attachments/assets/a8207397-6aa3-4b60-bc5e-0e535c2dadb3)

|Steps|Explaination |
|:-:|:-:|
|Download |The EuroSAT dataset is downloaded directly into the Colab environment.|
|Custom Dataset Class|A custom EuroSAT class is defined to handle the dataset, enabling the application of transformations|
|Image Transformations|Different transformations including random resizing, cropping, horizontal and vertical flips (for the training set), and normalization using ImageNet's mean and standard deviation.|
|Dataset Splitting |The dataset is randomly split into 70% for training, 15% for validation, and 15% for testing.|
|Data Loaders |PyTorch DataLoaders are created for each set to efficiently handle batching and shuffling during training.|

STEP 2 EXPLORATORY DATA ANALYSIS 


![image](https://github.com/user-attachments/assets/b0cf8a1b-e1ea-45c7-8046-0176c48438c5)

|Steps|Explaination |
|:-:|:-:|
|Class Distribution|A histogram is plotted to visualize the distribution of the 10 LULC classes in the EuroSAT dataset. This helps understand potential class imbalances|


STEP 3  MODEL DEVELOPMENT

![image](https://github.com/user-attachments/assets/74dc5562-79b2-4872-9a61-9345122d0215)

Resnet 50 is selected as Deep neural networks are difficult to train due to the problem of vanishing or exploding gradients (repeated multiplication making the gradient infinitively small). ResNet solves this by using shortcut connections that connect activation from an earlier layer to a further layer by skipping one or more layers as shown below. This allows for gradients to propagate to the deeper layers before they can be reduced to small or zero values.

|Steps|Explaination |
|:-:|:-:|
|ResNet-50 Selection|The ResNet-50 architecture is chosen for its ability to mitigate vanishing/exploding gradients through residual connections, enabling effective training of deep networks.|
|Fine-tuning|The pre-trained ResNet-50 model is fine-tuned on the EuroSAT dataset to adapt it to the specific task of LULC classification.|

ADDITIONAL STEPS 

|Steps|Explaination |
|:-:|:-:|
|Model Training|setting the stage for model training using the prepared data loaders and the chosen model architecture.|
|Model Evaluation|After training, the model would be evaluated on the test set to assess its performance|
|LULC Map Generation|The trained model could be used to generate LULC maps from new satellite images, showcasing the practical application of the classification model.|


Summary : [Colab Notebook](https://github.com/ParthDave111/Climate-Change-AI-Sumer-School-2024-/blob/main/Project%20Codes/LULC.ipynb)  provides a comprehensive workflow for LULC classification, covering data preparation, exploratory analysis, model selection, and the groundwork for training and evaluation.

Application 
This project can be applied to detect manual activities like urban expansion and deforestation 

![image](https://github.com/user-attachments/assets/dcc45e2e-29f8-4c11-a2fa-f41c0245b850)





Reference Links 

IPCC :https://www.ipcc.ch/
UN Climate Action :https://www.un.org/en/climatechange
Dr Zack Labe Website :https://zacklabe.com/
