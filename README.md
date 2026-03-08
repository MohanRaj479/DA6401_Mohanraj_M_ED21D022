# DA6401_ MOHANRAJ M
This is a part of DA6401 - Introduction to Deep Learning course Assignment 

# Assignment 1: Multi-Layer Perceptron for Image Classification

# Installation
Install wandb: 
Install Numpy:
Install Keras:

# 2.1 Data Exploration and Class Distribution
# Approach
- Visualization Strategy: Utilized wandb.Table to log 5 sample images per class, ensuring a balanced view of the dataset's diversity.
- Similarity Mapping: Identified visual overlaps in classes such as 4/9 and 3/5 in MNIST.
- Model Impact: Noted that visual similarity increases the probability of high-confidence misclassifications, requiring higher model capacity or better regularization.
- Data Prep: Integrated class-wise sampling logic to automate the exploration process directly from the NumPy arrays.

# 2.2 Hyperparameter Sweep
- Sweep Configuration: Define a dictionary containing ranges for learning_rate, batch_size, optimizer, and activation for wandb.sweep().
- Grid vs. Random Search: Use method: random to efficiently cover the high-dimensional search space across 100 runs.
- Parallel Coordinates Plot: Utilize the W&B UI to filter runs, looking for lines that converge at high validation accuracy to identify critical parameters like learning_rate.
- Best Config Selection: Identify the run with the highest val_accuracy and export its parameters for the final "Best Model" evaluation.




wnandb report link: https://wandb.ai/mohan6rj-indian-institute-technology-madras/DA6401_ED21D022_Homework1/reports/DA6401_Weights-Biases-Report_Homework1--VmlldzoxNjEzMzczNw/edit?draftId=VmlldzoxNjEzMzczNw==
