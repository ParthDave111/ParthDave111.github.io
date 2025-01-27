## Machine Learning Projects


## Machine Learning works [Orignal works]

## 1. K Mean Clustering Article

**Advantages**: Simple and easy to implement, also it scales well to the large datasets. In practice, K-means is efficient in terms of computation. As well as works well with linear clusters.

**Disadvantages:** There are some disadvantages in K-means cluster which includes the user to input the required number of clusters before running the analysis. Also, the model is  sensitive to the initial placement of centroids, which may lead to suboptimal solutions. In addition, the model is not suitable for non-linear clusters. Outliers can significantly skew results.

![image](https://github.com/user-attachments/assets/16192d9a-e4a8-462c-9802-e5020f9bee2b)

**Features:** which has assumed that the data is numeric, with NA values we should preprocess to handle them.
Guide:  with inputs, our dataset should be with numerical features, number of clusters  initialization method. And with output, the cluster labels would be given for each data point, centroids of the clusters, and inertia scores.

**Hyperparameters:** this includes the number of clusters or the number of groups. Secondly the initialization method which defines how centroids are chosen. In addition, the max iterations that control the maximum number of iterations allowed in our model and finally, the tolerance level which determines convergence threshold.

**Illustration**: analysis for three stock returns, BA, WMT and AAPL, from three different sectors, we
can identify how returns are different to each other. Below Elbow we have selected 3 as cluster
points, and returns are classified into three groups.

![image](https://github.com/user-attachments/assets/0692637c-cfff-4998-b5f9-6da25f70bf84)

Code : 




  
2. Principle component Analysis
3. Regression Tree

--------------

Machine learning is dominating almost every industry. To simply the application of Machine learning below are typical example of application .. and in coming years more can be added/developed.


| Application     |How | Algorithm  |
| --------- | --- | ----------- |
| Predictions |looks at past data, adjusts for trends, and smooths out random changes to make predictions| ARIMA,LSTM |
| Classification |finds patterns that separate one thing from another| XGBoost, logistical regression, SVM|
| Generation |Creates new things only from the things it saw before.|GANs, Transformers|
| Clustering |Groups similar things together without knowing what they are|K-means, hierarchical clustering|
|Recommendation  |suggests things based on your past behavior around similar things you liked. |Two-Tower models, collaborative or content-based filtering|
|Anomaly Detection |Identifies outliers or unusual patterns that do not conform to expected behavior|Isolation Forest, Autoencoders|
| Reinforcement Learning | Learns optimal actions through trial and error by maximizing rewards|Q-Learning, Deep Q-Networks|
| Dimensionality Reduction | Reduces the number of variables under consideration by finding the most important features.|PCA, t-SNE|
| [Casual Inference](Casualinference.md) |  Determines the cause-and-effect relationships from data.|Propensity Score Matching, Instrumental Variables|
| Ranking |  Orders items or instances according to their relevance or importance, often used in search engines or recommendation systems.|RankNet, LambdaMART|
|Time Series Analysis | Analyzes data points collected or recorded at specific time intervals|Seasonal decomposition, Exponential Smoothing, Prophet|
|Federated Learning |  Aggregates model updates from multiple devices without transferring raw data|Federated Averaging, Secure Aggregation|
|Meta Learning (Learning to Learn)|  Learns from a variety of tasks to develop a model that can generalize|Model-Agnostic Meta-Learning (MAML), Prototypical Networks|
|Active Learning| Focuses on uncertain or borderline examples to improve model performance|Uncertainty sampling, query-by-committee.|


## - Misc Machine Learning /Deep learning
  1. Explainable AI
  2. Computer Vision
  3. Natural Language processing
  4. Game AI [Alpha Zero]
  5. Explainable Reinforcement Learning
  6. Human-computer Interaction HCI
  7. Semantic Segmentation
  8. Knowledge graph
  9. Automated Machine Learning
  10. Cognitive Computing
  11. Emotional AI
  12. Algorithmic trading and AI









## Logistic Regression - Diabetes Prediction APP 
![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/36648fb3-7685-40bf-9a8e-4e011bcf02b1)

I have created a diabetes prediction application using logistic regression to predict weather the person has diabetes or not. 

**Project approach** :Data was collected from Kaggle and EDA was done. During EDA certain outliers excepts from"Insulin" columns were removed for analysis. Insulin sees to be one of the core parameter to judge diabetic condition.As insulin was higher , some of the column went through standard scaling process . Data was split into train -test in the ratio of 0.3 and logistic regression was applied. Hyperparamter tuning was done using grid search cv to find best parameters for logistic regression. Finally accuracy, precision and recall was calculated. 

PICKLE files were created for standard scaling and ML operation along with an UI based application file. To run this code directly, you have to open host file and upload 2 pickle file and application file 

Dataset: [here](https://www.kaggle.com/datasets/mathchi/diabetes-data-set)

Python code file :[here](https://github.com/ParthDave111/Diabetes-prediction-Logreg/blob/main/diabetes_prediction_logreg.ipynb)

**Business use case**: When a person get medical report he has to show it to Doctor to get final verdict. He/she can leverage such appplication and can determine if he is diabetic or not. Further this project can also be connected with any IOT apps which monitor certain parameters like glucose, insulin level to notify person to be cautious with sugar intake


## Decision Tree 

In the Decision tree, I have created 2 short project 

Decision Tree Classifier: - Worked on Iris Data set to feature decision tree classifier with post pruning and preprunning

![image](https://github.com/ParthDave111/ParthDave111.github.io/assets/123885634/43ce7574-1ff9-4890-98ab-d1cf07c45588)

Read code here: [Here](https://github.com/ParthDave111/Data-Science-/blob/main/Machine%20Learning/Decesion_Tree.ipynb)


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

![image](https://github.com/user-attachments/assets/cb4e8feb-c1d6-4586-905f-1b1a3b0498f4)



## While a man of pure intelligence may achieve the goal by the most casual of instructions, another may seek knowledge all his life and still remain bewildered - Ashtavakra"
