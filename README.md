# Deep-Learning-project
Binary classification problem. Train models for medical classification X-Ray Chest NORMAL and PNEUMONIA with PyTorch.
In general based on ideas from this article: "Automated Methods for Detection and Classification Pneumonia Based on X-Ray Images Using Deep Learning" https://arxiv.org/ftp/arxiv/papers/2003/2003.14363.pdf  | DOI: 10.1007/978-3-030-74575-2_14 

# Dataset
Where we gathered the dataset for the project.
https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia

# Data preparaiton 
In order to prepaire data for ANN models and local machine we resized RGB images to 64x64 and normalized them (mean: 0.485, 0.456, 0.406 and std:
0.229, 0.224, 0.225). Also, we used data augumenation techniques as 5 degree angle flipping. However, NORMAL chest images were 1500 among 4000 X-ray images. As a result dataset were inbalanced. To tackle it we incresed numbers of NORMAL labels via applying vertical and horizontal flipping. Finally, we had over 8000 images which were splited in 50/50 labels.

# Results
We trained 4 different ANN models as MLP, CNN, GoogLeNet and ResNet50. All of them sucsessfully trained on the dataset.
Our results shows that the best model is GoogLeNet with F1score equal 0.985 compare to baseline CNN and MLP models which have 0.968 and 0.967 score.

To increase our result we tried to use baggin technique. Our horizontal assembley contained all of the models to vote the best result. We made coefficient for MLP - 0.5, CNN - 0.5, ResNet50 - 0.5 and GoogLeNeT - 0.51 (because the best F1-score among other models). As a result we didn`t get better score compare to GoogLeNet. F1-score were 0.982 which is close to the best model.

# Futury study
In my opinion to get better score it is better try to implement a model which will located infected zone on images and shows probability of a PNEUMONIA anomaly or something else. If the probability was higher than an infected zone label that the model would classificate this images as not NORMAL and try to find what kind of annomaly is it.
At this article scientis were trying the idea above: "Viral Pneumonia Screening on Chest X-Rays Using Confidence-Aware Anomaly Detection" https://arxiv.org/pdf/2003.12338.pdf | DOI: 10.1109/TMI.2020.3040950 | PMID: 33245693
