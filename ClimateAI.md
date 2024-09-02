## Climate Change AI - All Projects related to sustainability and Climate Change

 [Back to Home Page](https://parthdave111.github.io/)



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

Application ::- 
This project can be applied to detect manual activities like urban expansion and deforestation 

![image](https://github.com/user-attachments/assets/dcc45e2e-29f8-4c11-a2fa-f41c0245b850)

## Project 2 Agile Modeling for Bioacoustic Monitoring

## Problem statement

The core problem this project addresses lies in biodiversity monitoring using large-scale, unlabeled audio data, as collected by inexpensive passive acoustic monitoring (PAM) devices. We present an integrated workflow for analyzing large unlabeled bioacoustic datasets, adapting new agile modeling techniques to the audio domain. The tools we provide enable users to adapt a classifier for a novel class (species, specific call type, etc...) with minimal overhead.

_Our goal is to allow experts to create classifiers for new sounds in less than an hour
_
**Xeno-Canto** is a vast online repository of bird, insect, and bat sounds. It's a citizen science project where volunteers worldwide upload and share recordings of wildlife sounds.

Google Perch :https://www.kaggle.com/models/google/bird-vocalization-classifier/tensorFlow2/bird-vocalization-classifier/4?tfhub-redirect=true

This project aims to demonstrate the use of **active learning** techniques to produce an audio classifier for novel tasks.

At a high level, active learning (aka "agile modeling") can be described as the process of bootstrapping dataset annotation by making use of an existing model, and then training a new classifier based on the bootstrapped dataset. The technique relies on a human-in-the-loop workflow to extract and produce a small subset of annotated data from the unlabeled dataset, which can then be used as training data for downstream tasks


This project can be utilized when 
1. The goal is to generate a custom classification model for a specialized task where enough labeled data is not enough to train a model from scratch
2.  access to the existing model is available that performs an adjacent task

## Key terminologies for the project /Learning

Agile Modeling
Agile modeling in the context of supervised machine learning can be described as “the process of turning any subjective visual concept into a computer vision model through real-time user-in-the-loop interactions” (Stretcu et al. 2023). In our setting, we go beyond the typical image and computer vision settings to explore the audio domain, where we transform a single labeled audio sample of a species vocalization into a bioacoustic classifier.

Transfer Learning
Transfer learning is a technique that relies on the reuse of a pre-trained model on a new task (different dataset from which it was trained). This technique assumes that the pre-training of the model produces a useful representation and knowledge that can be extended to the new task/setting. In the context of this tutorial, we use a model pre-trained on a large acoustic dataset of bird vocalizations (Xeno-Canto, focal recordings) to produce embeddings of a new soundscape dataset (passive recordings).

Intuition: in the context of avian bioacoustics, transfer learning is useful for building a general representation that can translate to specific species or geographical regions, particularly when labeled data is scarcer. Using a pre-trained model with transfer learning lowers the machine learning overhead for field experts and practitioners who seek to understand and interpret unlabeled data, such as that from passive acoustic monitoring (PAM).

Active Learning
Active Learning is a general term for an iterative, supervised ML technique that efficiently makes use of labeled data to “learn the labels” or classify unlabeled data. This learning setting is particularly helpful in scenarios where unlabeled data is abundant and producing labels for that data is costly, requires expert knowledge, lots of manual work, etc.

Embeddings
At their core, neural networks function by learning new representations of data that help make the underlying patterns in the dataset more obvious. These representations are called embeddings. Concretely, an embedding is a point (or vector) in a high dimensional space. Data points with embeddings that are close to each other are likely to share salient traits.

Bioacoustics and Biodiversity
Listening is a fantastic way to understand an ecosystem. An extremely broad collection of animals use sound to communicate--from owls to orcas, from bats to bonobos--which provides us with the opportunity to listen in and learn what animals are in an ecosystem.

We can also learn about the relationships between different animals: alarm calls indicate the presence of silent predators, and can even contain clues about what kinds of predators are nearby. We can measure how vocalizations change in response to differences in the natural environment (elevation, temperature, geographic location, seasonality) or in response to human interventions (restoration programs, logging, proximity to highways, etc.).

## Main challenge of this project
Bioacoustic surveys can generate thousands or even millions of hours of audio, far more than experts could ever listen to. As a result, we require machine learning tools which multiply the efforts of these experts. These tools must also allow us to work with staggering amounts of audio data efficiently.

Additionally, new problems are appearing all the time: no single classifier is going to cover all the bases. There are thousands of species for which we don't have sufficient training data for traditional ML classifier training, especially in tropical areas where biodiversity is the greatest. Furthermore, we are often concerned with different types of vocalizations. If we can differentiate between juvenile and adult calls, we can measure a population's reproductive health efficiently. In other cases, different calls can help determine if an endangered species is nesting in an area (requiring a high degree of protection) or simply passing through the area. Needless to say, training data for these highly-specific problems often simply does not exist.

As a result, training a single mega-classifier is not enough: We require flexible tooling which can capture new kinds of insights efficiently.

## Work In Progress

Project 2 - NLP models for climate policy analysis 



Project 3 - Forecasting EL nino with Machine learning


Project 4  Reducing Climate impact when training ML MODEL [ Project based on Estimating carbon footprint of BLOOM 176B parameter LLM [Paper Link ](https://jmlr.org/papers/volume24/23-0069/23-0069.pdf)

