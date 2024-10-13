# **Animal Classification using Convolutional Neural Networks (CNN)**

# **Overview of the data**
This project explores the classification of images into two categories: 
**Wild** and **Domestic** animals using a deep learning approach. Various optimization 
techniques were implemented and compared to improve the performance of a Convolutional Neural Network (CNN).
These include regularization methods such as L1 and L2 regularization, dropout, and early stopping mechanisms.
The project concludes with a comprehensive analysis of the model performance, utilizing metrics such as accuracy, confusion matrix, and validation accuracy.

## **Dataset**
The dataset used consists of images categorized into two classes:

- Wild Animals
- Domestic Animals
- The images were preprocessed by resizing them to a standard size of 150x150 pixels 
and normalizing the pixel values by scaling between 0 and 1.

## **Model Architectures and Optimization Techniques**
Multiple models were developed using different optimization techniques.
Each technique aimed to enhance the model's accuracy, prevent overfitting, and improve generalization.

## **1. Vanilla Model**
The baseline model was constructed using the following layers:

- Three convolutional layers with increasing filter sizes (32, 64, 128)
- Max-pooling layers after each convolutional layer
- A fully connected dense layer with 128 units and ReLU activation
- Output layer with a sigmoid activation for binary classification

![Screenshot 2024-10-13 053126](https://github.com/user-attachments/assets/0c2ab484-f761-431a-a0c4-06107770b1f8)


### **Results and Findings**
- Accuracy improved progressively over epochs, achieving a validation accuracy of 97.55% and test accuracy of 79.34%.
- However, the error distribution from the confusion matrix could indicate misclassification
between wild and domestic animals due to the model's inability to generalize on unseen data.


## **2. L1 Regularization and Early Stopping**
- L1 regularization was introduced to the model to penalize large weights and control overfitting.
- Additionally, early stopping was employed to halt training if no improvement in validation accuracy was observed for several epochs.

![Screenshot 2024-10-13 053607](https://github.com/user-attachments/assets/2980a7e1-1ec5-4924-b993-68b19f90f338)


### **Results:**
- Despite the introduction of L1 regularization and early stopping, the model struggled,
with validation accuracy fluctuating around 52.5%. 
The early stopping feature helped in avoiding unnecessary training, but the L1 regularization 
did not improve the performance significantly.
- This led to the model underfitting the data, especially for the minority class, as shown in the confusion matrix above.

## **3. L1 Regularization (No Early Stopping)**
To test the isolated effect of L1 regularization, another model was trained without the early stopping mechanism.

![Screenshot 2024-10-13 162910](https://github.com/user-attachments/assets/bf4c694c-5148-413e-882d-909c3029f52e)


### **Results:**
- Just like L1 regularization with early stopping and Adam Optimizer, the model still can't predict correctly.
 In this case, we will try another optimization method and see.
- The sparsity from L1 regularization still prevents the model from achieving higher accuracy.
Recall might be particularly low, as evidenced by the imbalance in the confusion matrix.

## **4. L2 Regularization (No Early Stopping)**
This model uses L2 regularization (also known as ridge regression) to prevent overfitting by penalizing large weights more gradually than L1 regularization.

![Screenshot 2024-10-13 055228](https://github.com/user-attachments/assets/d8b76e4c-0cc7-4127-855d-03077c6c5d8f)

### **Key Highlights of Training:**

- **Epochs:** Trained for 20 epochs without early stopping, allowing the model to fully learn from the training data.
- **L2 Regularization Impact:** L2 regularization smoothed the loss curve, preventing the model from overfitting too early while still allowing it to capture essential patterns in the data.

### **Training Progress:**

- **Accuracy Improvement:** The model's accuracy increased from around 60% to over 82%, outperforming the previous models.
- **Validation Accuracy:** Validation accuracy reached its peak at around 75%, showing that the model was generalizing well.
- **Loss Curve:** Unlike the vanilla model, the validation loss continued to decrease steadily, indicating that the model was learning effectively and avoiding overfitting.

### **Validation Performance:**

- **Confusion Matrix:** The confusion matrix showed fewer false positives and false negatives compared to earlier models, indicating better class separation.
- **Specificity:** This model had the highest specificity, meaning it was particularly good at correctly identifying domestic animals.
- **F1 Score:** The F1 score improved significantly, indicating better balance between precision and recall.

## **5. L2 Regularization, RMSprop Optimizer, and Early Stopping**
In this model, the optimizer was switched from Adam to RMSprop, and early stopping was reintroduced to further enhance performance.

![Screenshot 2024-10-13 055512](https://github.com/user-attachments/assets/6a22c45d-717e-4627-a24e-765ad1c0629c)


### **Results:**
- While the performance improved slightly, the validation accuracy did not surpass the previous L2 regularization model,
showing that changing the optimizer and adding early stopping was not as impactful in this context.

## **6. L2 Regularization and Dropout**
To improve generalization further, dropout layers were added to the network to randomly switch
off neurons during training and reduce reliance on specific features.

![Screenshot 2024-10-13 055800](https://github.com/user-attachments/assets/93af8dc0-ce47-4b52-9269-7be0ec2282ed)


### **Key Highlights of Training:**
- **Dropout:** Dropout helped mitigate overfitting, but when used in combination with L2 regularization, it sometimes led to underfitting.

**Training Progress:**
- **Accuracy:** The model’s accuracy hovered around 68%, which was lower than other models using L2 regularization without dropout.
- **Validation Accuracy:** Validation accuracy remained moderate at 67%, and the model struggled to surpass that.
Validation Performance:
- **Confusion Matrix:** Showed higher false negatives than the best model, indicating that the model had trouble identifying domestic animals.
- **F1 Score:** The F1 score was moderate, with the model underperforming compared to other L2 regularized models.
