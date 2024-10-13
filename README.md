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
The images were preprocessed by resizing them to a standard size of 150x150 pixels 
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

### **Results:**
- Without early stopping, the model was able to learn more from the training data, 
leading to an improvement in performance.
- However, the sparsity from L1 regularization still prevents the model from achieving higher accuracy.
Recall might be particularly low, as evidenced by the imbalance in the confusion matrix.

## **4. L2 Regularization (No Early Stopping)**
L2 regularization, which discourages large weight values by penalizing them, 
was tested as another form of regularization without early stopping.

![Screenshot 2024-10-13 055228](https://github.com/user-attachments/assets/d8b76e4c-0cc7-4127-855d-03077c6c5d8f)


### **Results:**
- This model effectively controls overfitting while maintaining model complexity,
leading to the best results across all key metrics.
- The confusion matrix reflects a more balanced distribution of errors, 
and the F1 score suggests that both precision and recall are improved.

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


### **Results:**
- The combination of L2 regularization and dropout achieved consistent results, with validation accuracy around 70%.
While not outperforming the best L2 model, this technique effectively reduced overfitting.
