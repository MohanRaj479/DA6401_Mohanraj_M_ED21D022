# DA6401_ MOHANRAJ M
This is a part of DA6401 - Introduction to Deep Learning course Assignment 

# Assignment 1: Multi-Layer Perceptron for Image Classification
2.1 Data Exploration and Class Distribution
Visualization Strategy: Utilized wandb.Table to log 5 sample images per class, ensuring a balanced view of the dataset's diversity.

Similarity Mapping: Identified visual overlaps in classes such as 4/9 and 3/5 in MNIST, and Shirt/Coat in Fashion-MNIST.

Model Impact: Noted that visual similarity increases the probability of high-confidence misclassifications, requiring higher model capacity or better regularization.

Data Prep: Integrated class-wise sampling logic to automate the exploration process directly from the NumPy arrays.

wnandb report link: https://wandb.ai/mohan6rj-indian-institute-technology-madras/DA6401_ED21D022_Homework1/reports/DA6401_Weights-Biases-Report_Homework1--VmlldzoxNjEzMzczNw/edit?draftId=VmlldzoxNjEzMzczNw==
