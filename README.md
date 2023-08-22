# Intrusion-Detection-using-Ensemble-Learning


The massive usage of network is increased rapidly by storing and sharing lots of important data and by development in technology.
The range of human beings using internet for storing or gaining access to essential data has increased. As a result,the need to secure the data integrity, and confidentiality has also increased. 
Although, to secure data transmission attempt have made, the attacks to breach the network has continued to evolve.
The motivation behind the development and implementation of IDSs is the increasing number and sophistication of cyber attacks. 

The two most popular types of intrusion detection systems (IDS) are host-based (HIDS) and network-based (Network IDS)[2]. Network-based IDS focuses only on network traffic in an effort to detect unauthorised, illegal, and unusual conduct. In contrast, HIDS makes an effort to spot unauthorised, illegal, and unusual conduct on a particular device. In this paper, they’ve propose a unique approach for network-based intrusion detection systems. Most intrusion detection systems use one of the two detection techniques, either anomaly-based or signature-based. An anomaly-based IDS finds deviations from "normal" behaviour and identifies them. When there are no aberrant behaviours, it gains knowledge from the regular data that is gathered. A signature-based IDS, on the other hand, looks for pre-configured and pre-planned attack patterns in the network traffic. 

 UNSW-NB15:
The UNSW-NB15 computer network security dataset was released in 2015(Moustafa & Slay, 2015)[8]. This dataset includes 2,540,044 instances of genuine, contemporary, regular and abnormal network activity (commonly referred to as assaults).
The direction, inter-packet length, and inter-arrival durations are the three most important properties in the flow-based feature formulation: Total duration (dur) and destination-to-source-time-to-live (dttl) are two examples of flow-based features. Three categories—basic (6–18), content (19–26), and temporal (27–35)—are used to group the characteristics. General-purpose features are defined as features 36 through 40, whereas connection features are defined as features 41 through 47. While two features in the category of connection features depict the characteristic of the connection among 100 sequentially ordered records, the category of general purpose features consists of those qualities that are intended to illustrate the purpose of a single record. 

![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/4f92ddc5-f323-4d38-908e-6fb6c2a510bc)

NSL-KDD:
The KDD cup99 dataset was upgraded to NSL-KDD in order to fix a number of problems[9] with the original version. In addition to other advantages, this data collection can be used by researchers to compare various intrusion detection system (IDS) approaches, build an intrusion detection system (either host-based or network-based), and run experiments in the field of cyber security. This dataset comprises of 1,48,517 The types of attackers in this dataset have been categorized into four main attack types.

![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/ae9e0017-248f-45c4-a034-b5763b3e15f1)


Dataset Preprocessing

NSL-KDD

Started with cleaning of dataset by handling the missing values through filling them with appropriate values and also corrected any inconsistent or erroneous data present.
Added columns to the dataset, ‘target’ containing different attacks and ‘Attack type’ containing different attack classes.
Then we used the dataset in two different ways:
First, which contained only numeric features, and the labels converted to binary labels
Second, containing all the features, in which the non-numeric features were encoded later.

Both these experiments were done for both multi label as well as binary label dataset.


Now analyzing rest of the features as we cannot consider 42 columns for training since it would lead to increase in correlation between dependent variables which leads to decrease in accuracy
Combined various attack types under four categories named as DoS, Probe, R2L & U2R.
Converted the object data types to numeric features and also dropped some columns which were not necessary in the training process such as service, destination host name etc.
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/1307a9ce-b6f7-4cc5-97bc-2cc72d1da3ea)

We also need to analyze the dataset based on correlation between different features
The figure here depicts the correlation plot between all the features we are finally considering after data preprocessing
And then proceeded to discard the features which highly correlated with each other
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/a1e13b29-dc00-4b3a-9917-6da1aed2e817)


Dataset Preprocessing

    II.     UNSW-NB15
Used almost the same steps that are performed in preprocessing NSL-KDD but there were few more steps involved in this dataset and also the categorical features were a bit different.
Here the types of attackers were already sectioned into 10 types of attacks so we have considered here 10 ways in which the final result would be classified instead of 5 types mentioned in the NSL-KDD dataset.
The “proto” feature has a total of 133 types of protocols mentioned, so instead of mapping it to integer values, we have performed one-Hot Encoding on this categorical data.
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/7ca42072-186a-4b5b-b3e7-8b463b069167)

Same goes with this dataset as well that we need to remove the features which are highly correlated with other features 
The white grid in the figure depicts the most high correlation between two features and according to that we can work with them

![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/64d1e9bd-5dd3-4e99-8870-6cc58ef8b900)

III. Feature Extraction
For both the datasets we also performed PCA (principal component analysis) which works as a dimensionality reduction technique used in machine learning and statistics. 
It is used to reduce a big set of linearly correlated variables into a smaller set of variables known as primary components. 
PCA works by identifying patterns in the correlations between variables in the data and transforming the original variables into new, uncorrelated variables that capture the most important patterns in the data. 


Modeling & Evaluation

A. First Approach
After preprocessing, feature extraction and feature engineering from the dataset now we move forward to the model training and evaluation part
In this first approach we have divided the dataset into three parts that are train, validation and test. And then applied the two machine learning algorithms on the preprocessed dataset that are SVM and Random Forest for training the dataset

3.3.1 First Approach:
We have applied two machine learning algorithms on the preprocessed dataset that are SVM and Random Forest, and obtained a testing accuracy of 83.24% and 87.22%, respectively. The results of both classifiers for the UNSW-NB15 dataset are mentioned below in Fig 7.
For the NSL-KDD dataset, we obtained a testing accuracy of 93.02% for SVM and 99.24% for RF. 
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/4f5e8951-fdf8-47ad-bc3c-a4db9b2cba87)
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/f0910cb9-656e-4aee-a07a-23bda54b60f5)

Second Approach
As it we observed in the first approach that, the SVM model achieved a lower accuracy than Random Forest. To improve the accuracy further, we used a different machine learning approach, which is the Ensemble machine learning technique. 
We’ve used the Extra Tree classifier and XGBoost classifier, which are based on the concept of Ensemble Machine Learning Techniques. 
Then these sets of classifiers were applied to both the Binary label and Multi-label datasets. And we also applied the Trust Score algorithm for the prevention of intrusions into the system. 

Trust Score Algorithm: It is a measure of how confident the model is in its prediction for a given sample, a computational method used to evaluate and quantify the level of trustworthiness or reliability of a person or system
In the case of Intrusion detection it is designed to assess the trustworthiness or reliability of network traffic and detect potential security threats or attacks. 
Then a trust score is generated based on model evaluation which helps in distinguishing between normal and malicious activities, allowing the system to focus on the most suspicious or high-risk events.

Working of the proposed trust score algorithm:

Steps:
We predict the probability of each class for each sample in the X_test data. This method returns an array of shape `(n_samples, n_classes) ` containing the predicted probabilities.
The function initializes an array called trust_scores with zeros, which will store the trust score for each sample in X_test. 
The function then iterates over each sample in X_test. For each sample, it retrieves the predicted class probabilities from the y_proba array 
Then finds the maximum probability from the class of probabilities which represents the highest confidence level among all the predicted classes for that particular sample.
5. The function then calculates the trust score for the current sample by   dividing the maximum probability by the sum of all the class probabilities. 
  6. This is done to determine the relative confidence level of the highest predicted class compared to the other classes.
  7. The trust score for the current sample is stored in the corresponding index of the trust_scores array.
  8. Once all samples in X_test have been processed, the function returns the trust_scores array.

![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/c71100b1-242c-4b92-b437-dda96dcbf362)

Example:
Suppose we have a binary classification problem, and X_test contains three samples with the following predicted class probabilities:
                                                                  X_test = [[0.3, 0.7],  [0.6, 0.4],  [0.8, 0.2]]     
Assuming model is a trained classifier, the calculate_trust_scores function will compute the trust scores for each sample as follows:
trust_scores = [0.7 / (0.3 + 0.7),     -> Sample 1: 0.7 (highest probability) / 1.0 (sum of probabilities)
                0.6 / (0.6 + 0.4),     -> Sample 2: 0.6 (highest probability) / 1.0 (sum of probabilities)
                0.8 / (0.8 + 0.2)]     -> Sample 3: 0.8 (highest probability) / 1.0 (sum of probabilities)

Therefore, the resulting trust_scores array will be [0.7, 0.6, 0.8].


Modeling & Evaluation

B. Second Approach
XGBoost: The architecture of this is based on the concept of decision trees, which are used as the weak learners.
It sequentially constructs a number of decision trees, each of which attempts to fix the flaws in the one before it. 
The trees are built using a process called boosting, where the data points that are misclassified by the previous tree are given higher weights
This process is repeated iteratively until the residuals are minimized. 
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/c14f9164-2e7c-446e-b38d-7fba65542745)

Extra Tree Classifier: This algorithm is similar to XGBoost as it is based on a decision tree but the main difference between these two algorithms is that XGBoost selects features based on their importance. 
Extra Trees selects features randomly, similarly in the case of bias-variance tradeoff, XGBoost has a higher variance than Extra Trees. 
Extra Trees, on the other hand, has a higher bias due to its random splits, but it has a lower variance and can be more robust to noise. 
In situations where fast training and robustness to noise is necessary we use Extra Tree classifier in place of XGBoost. 
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/07a28225-4122-4015-a00b-d58a8214c78d)

Result and Performance Analysis: 
In this section, we will be discussing the results after experimentations with Ensemble based Machine learning techniques and some performance based metrics of the model and latency, runtime and space complexity of the algorithm used. Performance analysis of the proposed Intrusion Detection and Prevention System is specified, including latency, runtime, and space complexity of the trust score algorithm.

3.4.1 Results of NSL-KDD dataset:
We have analyzed various evaluation metrics of the two ensemble learning algorithms for NSL-KDD dataset which are shown below. We have here analyzed the accuracies of both Binary and Multi class labels for better understanding. It can be clearly observed from the results that XGBoost is achieving more accuracy in comparison to Extra Tree classifier as shown in Table 2. This might be occurring as XGBoost uses gradient boosting technique for feature selection, splitting of dataset and for bias-variance tradeoff whereas ExtraTree is randomly all these processes. 

Table 2. Comparison of accuracies achieved for NSL-KDD dataset
Classifiers
Binary label
Multi-label
XGBoost
99.62%
98.63%
Extra Tree
97.83%
95.37%



We have described in the Fig.12 firstly the evaluation metrics results obtained for Multi-Classification of Extra Tree based classifier, then the heat map for the same from which, it can be observed that the classes predicting accurate results are much more than wrong predictions which means that model fitted properly and is giving good predictions and then finally the trust scores generated for network data points based on the algorithm formulated for calculation.
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/c3e904e7-5bf5-4fe5-9df5-4819c911fa1f)

Visual representation of XGBoost classifier evaluation metrics, heatmap and trust scores generated are shown in Fig. 13 below. It is noticeable here that values of true positive and true negatives are much higher than false positive and false negative which implies that the model is predicting a total of 36992 values correctly.
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/0dab16c6-5016-4174-921c-2772b7336cca)

Results of UNSW-NB15 dataset:
Similarly, to the evaluation of the NSL-KDD dataset, we used a variety of methodologies to analyse the results of model training on this dataset. The Table 3 given below represents the accuracy analysis of both the machine learning algorithms for binary and multi-class labels, through which it can be observed that in this case also XGBoost is working comparatively better than the other algorithm that we have considered because of the reasons we have mentioned previously.

Table 3. Comparison of accuracies achieved for UNSW-NB15 dataset

Classifiers
Binary label
Multi-label
XGBoost
97.2%
88.7%
Extra Tree
94.8%
86.21%






In the Fig 14 shown below we have stated the classification report after the training and validation of the XGBoost classifier, heatmap obtained from which it can be formulated that the number of wrong predictions are lesser than the correct ones and finally the trust scores generated.
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/5d0a3a2b-7bda-4faa-8edd-e8b360f2ed5c)

The heatmap and trust scores generated by the XGBoost classifier are represented visually in Fig. 15 below. Here, it is clear that true positive and true negative values are significantly higher than false positive and false negative values but still can be considered as negligible in this case, suggesting that the model accurately predicts a total of 48783 values and 2752 wrong ones. 
![image](https://github.com/shristy15/Intrusion-Detection-using-Ensemble-Learning/assets/77338956/a6e5f9ac-40fa-4035-9fc1-ac32622a2ef4)


Performance Analysis:
After testing the data set samples on the Trust score algorithm proposed and Ensemble Machine Learning Techniques, we received the performance results as follows:
The Latency was recorded as 0.5275 seconds, indicating the time taken for the algorithm to perform its task. 
The Runtime, on the other hand, was recorded as 68.93 seconds, indicating the total time taken for the entire process, including loading data, preprocessing, training, and evaluation. 
The Memory Usage was 727.98 MB, indicating the amount of memory utilized during the execution of the algorithm.
It can be inferred from the above results that latency of the trust score algorithm is relatively low, at around 0.53 seconds, indicating that the code executes relatively quickly. It's worth noting that these numbers are specific to the input data and model used in this example and may vary depending on the specifics of the ML algorithm and the hardware and software environment in which the code is executed.
















