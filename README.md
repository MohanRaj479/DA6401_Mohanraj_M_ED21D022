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
  
  The wandb report link for the MNIST samples visulaization https://wandb.ai/mohan6rj-indian-institute-technology-madras/DA6401_ED21D022_Homework1/runs/qw9ga45v/panel/kqf3jscun?nw=nwusermohan6rj

# 2.2 Hyperparameter Sweep
# Approach
- Sweep Configuration: Define a dictionary containing ranges for learning_rate, batch_size, optimizer, and activation for wandb.sweep().
- Grid vs. Random Search: Use method: random to efficiently cover the high-dimensional search space across 100 runs.
- Parallel Coordinates Plot: Utilize the W&B UI to filter runs, looking for lines that converge at high validation accuracy to identify critical parameters like learning_rate.
- Best Config Selection: Identify the run with the highest val_accuracy and export its parameters for the final "Best Model" evaluation.

# 2.3 The Optimizer Showdown
# Approach
- Controlled Testing: Fix the architecture (3 layers, 128 neurons, ReLU) and only vary the optimizer class (SGD, Momentum, NAG, RMSProp).
- Convergence Logging: Log train_loss at every iteration to visualize the steepness of the curve in the first 5 epochs.
- Fastest Minimizer: Identify the optimizer (likely NAG or RMSProp) that reaches the lowest loss threshold earliest.
- Theoretical Justification: Note that RMSProp uses a moving average of squared gradients to normalize the learning rate, preventing oscillations in steep directions.


wnandb report link: https://wandb.ai/mohan6rj-indian-institute-technology-madras/DA6401_ED21D022_Homework1/reports/DA6401_Weights-Biases-Report_Homework1--VmlldzoxNjEzMzczNw/edit?draftId=VmlldzoxNjEzMzczNw==
