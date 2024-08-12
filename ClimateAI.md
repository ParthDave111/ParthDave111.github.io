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
|Steps|Explaination |
|Download |The EuroSAT dataset is downloaded directly into the Colab environment.|
|Custom Dataset Class|A custom EuroSAT class is defined to handle the dataset, enabling the application of transformations|
|Image Transformations|Different transformations are applied to the train, validation, and test sets, including random resizing, cropping, horizontal and vertical flips (for the training set), and normalization using ImageNet's mean and standard deviation.|
|Dataset Splitting |The dataset is randomly split into 70% for training, 15% for validation, and 15% for testing.|
|Data Loaders |PyTorch DataLoaders are created for each set to efficiently handle batching and shuffling during training.|






Summary : [Colab Notebook](https://github.com/ParthDave111/Climate-Change-AI-Sumer-School-2024-/blob/main/Project%20Codes/LULC.ipynb)  provides a comprehensive workflow for LULC classification, covering data preparation, exploratory analysis, model selection, and the groundwork for training and evaluation.





Reference Links 

IPCC :https://www.ipcc.ch/
UN Climate Action :https://www.un.org/en/climatechange
Dr Zack Labe Website :https://zacklabe.com/
