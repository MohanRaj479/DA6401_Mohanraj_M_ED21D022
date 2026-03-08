# DA6401_ MOHANRAJ M
This is a part of DA6401 - Introduction to Deep Learning course Assignment 

# Assignment 1: Multi-Layer Perceptron for Image Classification

# Installation
Install wandb: 
Install Numpy:
Install Keras:

# 2.1 Data Exploration and Class Distribution
# Approach
- Visualization Strategy: Utilized wandb.Table to log 5 sample images per class, ensuring a balanced view of the MNIST dataset's diversity.
- Similarity Mapping: Identified visual overlaps in classes such as 4/9 and 3/5 in MNIST.
- Model Impact: Noted that visual similarity increases the probability of high-confidence misclassifications, requiring higher model capacity or better regularization.
- Data Prep: Integrated class-wise sampling logic to automate the exploration process directly from the NumPy arrays.
  
  The wandb report link for the MNIST samples visulaization can be seen [here](https://wandb.ai/mohan6rj-indian-institute-technology-madras/DA6401_ED21D022_Homework1/runs/qw9ga45v/panel/kqf3jscun?nw=nwusermohan6rj)

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
  
Code link available for this question is - https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/3_optimizer_showdown

# 2.4 Vanishing Gradient Analysis
# Approach
- Activation Comparison: Train two identical networks, one with Sigmoid and one with ReLU, using the RMSProp optimizer.
- Gradient Tracking: Access the grad_W (or dW) attribute of the first hidden layer and log its L2 norm using np.linalg.norm(layer.grad_W).
- Vanishing Observation: Observe the Sigmoid plot where the norm approaches zero rapidly as the network gets deeper or training progresses.
- ReLU Advantage: Use the plots to show that ReLU maintains a constant gradient for positive inputs, avoiding the "saturation" regions of Sigmoid.

Code link available for this question is -  https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/4_vanishing_gradient

# 2.5 The "Dead Neuron" Investigation
# Approach
- Activation Logging: Use wandb.Histogram to log the output of the ReLU layer after the forward pass.
- Identifying Dead Neurons: Look for a large spike at exactly 0.0 in the activation distribution; this indicates neurons that never fire due to a high learning rate.
- Activation Comparison: Compare this with Tanh, which produces a zero-centered distribution but suffers from saturation rather than "death."
- Convergence Explanation: Explain that dead ReLU neurons have zero gradients and can never recover, whereas Tanh neurons only slow down.

Code link available for this question is - https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/5_The_dead_neuron

# 2.6 Loss Function Comparison
# Approach
- Standardized Setup: Use the same learning_rate and architecture to train one model with MSE and another with Cross-Entropy.
- Loss Tracking: Plot both training curves on the same chart to compare the "plateau" behavior.
- Mathematical Advantage: Explain that Cross-Entropy combined with Softmax cancels out the saturation terms in the gradient, leading to steeper gradients when the error is high.
- Optimization Efficiency: Show that MSE results in slower initial learning because the gradient disappears when the prediction is very wrong.

Code link available for this question is - https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/6_Loss_comparison

# 2.7 Global Performance Analysis
# Approach
- Overlay Plots: Use the W&B "Run Overlays" feature to plot train_accuracy vs. test_accuracy for all 100+ sweep runs.
- Overfitting Identification: Target runs where the training accuracy is near 1.0 but test accuracy is significantly lower (e.g., < 0.85).
- Gap Interpretation: Define the gap as "Generalization Error," indicating the model is memorizing training noise rather than learning universal features.
- Regularization Necessity: Conclude that high-gap runs require weight_decay or dropout to improve test-set performance.

# 2.8 Error Analysis
# Approach
- Matrix Generation: Run wandb.log({"conf_mat": wandb.plot.confusion_matrix(...)}) using the predictions from the test set.
- Failure Gallery: Filter test_preds = y_test and log these specific images with captions showing Actual vs Predicted.
- Error Clustering: Observe which digit pairs (like 4/9) are most frequently confused.
- Creative Visualization: Plot a heatmap of the average "incorrect" image to see the common noise pattern that fools the model.

Code link available for this question is - https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/8_Error%20analysis 

# 2.9 Weight Initialization & Symmetry
# Approach
- Initialization Logic: Compare a model where W = np.zeros() with one where W uses Xavier scaling.
- Neuron Gradient Tracking: Track layer.grad_W[0, :5] to isolate 5 specific neurons in the first hidden layer.
- Symmetry Observation: Plot these 5 gradients; in the "Zeros" run, they will appear as a single overlapping line on W&B.
- Mathematical Necessity: Conclude that "Symmetry Breaking" via random initialization is required so neurons can follow different gradient paths and learn distinct features.

Code link available for this question is - https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/9_Weight_init

# 2.10 Fashion-MNIST Transfer Challenge
# Approach
- Data Normalization: Scale pixel values to [0, 1] and use Mini-Batch Gradient Descent (size 64) to handle the increased data variance.
- Configuration Transfer: Select the top 3 configs from MNIST (NAG and Momentum) and test them on the clothing dataset.
- Performance Gap: Note that accuracy is lower on clothing than digits (e.g., 88% vs 98%) due to higher internal texture complexity.
- Capacity Tuning: Increase hidden_neurons (128 or 256) to provide the model with more "memory" to distinguish between similar categories like Pullovers and Coats.

Code link available for this question is below - https://github.com/MohanRaj479/DA6401_Mohanraj_M_ED21D022/blob/main/10_fashion_MNIST


# wnandb report link: 
[ED21D022_wandb report](https://wandb.ai/mohan6rj-indian-institute-technology-madras/DA6401_ED21D022_Homework1/reports/DA6401_Weights-Biases-Report_Homework1--VmlldzoxNjEzMzczNw/edit?draftId=VmlldzoxNjEzMzczNw==)
