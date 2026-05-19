# Lisondra-MarjorieMae_LW5_Comparative_Analysis

###### [Google Collab Link - LW5](https://colab.research.google.com/drive/1AV6cNlVQkdtEW5cPAal8yvzosnJYpJ22?usp=sharing)

---

## PART 12: Performance Comparison Table

| Model - Sample | Train Accuracy | Train Loss | Test Accuracy | Test Loss | Precision | Recall | F1-score | ROC AUC |
|---|---|---|---|---|---|---|---|---|
| Pre-Trained Model 1 (VGG16) | 80.07% | 0.6751 | 90.81% | 0.4593 | 0.9114 | 0.9087 | 0.9080 | 0.9950 |
| Pre-Trained Model 2 (ResNet50) | 97.77% | 0.1155 | 98.40% | 0.0714 | 0.9830 | 0.9830 | 0.9828 | 0.9997 |
| Pre-Trained Model 3 (EfficientNetB0) | 5.27% | 2.9956 | 5.23% | 2.9954 | 0.0025 | 0.0500 | 0.0047 | 0.5674 |
| Model from Teachable Machine | 99.5% | 0.005 | 99.5% | 0.25% | 0.0026 | 0.0026 | 0.0026 | 0.4685 |
| Your 1st Model (LW3) | - | - | 90.89% | - |  0.9141 |  0.9046 | 0.9047 | 0.9956 |
| Your 2nd Model Enhancement (LW3 Enhanced) | 57.96% | 0.0520 | 70.57% | 0.3807 | 0.7292 | 0.7047 | 0.7078 | 0.9646 |
| Your 3rd Model (LW4 Transfer Model) - The Good Model | 98.48% | 0.0474 | 97.13% | 0.1183 | 0.9721 | 0.9707 | 0.9705 | 0.9994 |

---

## Guide Questions (Student Reflection & Explanation) 

## A. Model Performance

###  1. Which pre-trained model achieved the highest accuracy? Why?
  <div align="justify">
    The pre-trained model that achieved the highest accuracy was ResNet50 with an accuracy of 98.40%. This high performance can be attributed to its deep residual architecture, which enables the model to learn complex botanical features more effectively while minimizing vanishing gradient problems during training.
  </div>

###   2.  Which model had the lowest performance? What could be the reason?
  <div align="justify">
    The model with the lowest performance was the Teachable Machine model with only 0.25% accuracy. Among the Keras-trained models, EfficientNetB0 had the lowest performance at 5.23%. This poor performance may have been caused by sensitivity to preprocessing and scaling requirements. In the case of the Teachable Machine model, the results suggest a possible label mapping mismatch or export configuration issue.
  </div>

###    3. How did loss values compare across models?
   <div align="justify">
     In terms of loss values, ResNet50 obtained the lowest Test Loss of 0.0714, indicating strong confidence and accurate predictions. VGG16 followed with a Test Loss of 0.4593, while EfficientNetB0 recorded a high Test Loss of 2.9954, showing that it failed to converge toward a reliable solution.
   </div>
  
## B. Evaluation Metrics
###  4. Why is accuracy not enough to evaluate a model?
  <div align="justify">
   Accuracy alone is not sufficient to evaluate a model because it does not fully reflect the quality of predictions, especially when a model fails to generalize properly. For example, although EfficientNetB0 achieved 5.23% accuracy, its Precision was only 0.0025, indicating that the model was heavily biased toward predicting a single class and could not effectively distinguish among plant species.
  </div>
  
###  5. Which model had the best F1-score? What does it indicate?
  <div align="justify"> 
    ResNet50 achieved the best F1-score with a value of 0.9828. This indicates that the model maintained an excellent balance between Precision and Recall, meaning it was both reliable in its predictions and effective at identifying all relevant plant species.
  </div>

###  6. How did Precision and Recall differ across models?
  <div align="justify"> 
    The Precision and Recall values differed significantly across the models. ResNet50 maintained a balanced Precision and Recall of 0.9830, demonstrating consistent classification performance. VGG16 showed slightly lower but still balanced values at approximately 0.91. In contrast, EfficientNetB0 and the Teachable Machine model had Precision and Recall values close to zero, indicating a major failure in generalization and classification capability.
  </div>

## C. Confusion Matrix Analysis 

###  7. Which classes were frequently misclassified?
   <div align="justify">
     Based on the confusion matrix analysis, the class “pickerelweed” was frequently misclassified in the VGG16 model, as shown by its Recall score of only 0.75. Additionally, “water_stargrass” recorded a lower Precision score of 0.80, suggesting confusion with similar aquatic plant species.
  </div>
  
###  8. What patterns did you observe in the confusion matrix?
   <div align="justify">
     The confusion matrix of ResNet50 displayed a very clean diagonal pattern, indicating highly accurate predictions across classes. On the other hand, the VGG16 confusion matrix revealed visible confusion among aquatic plants, particularly between “pickerelweed” and “arrow_arum,” which suggests similarity in their visual features.
  </div>
  
## D. ROC and AUC
###   9. Which model had the highest AUC score?
   <div align="justify">
     ResNet50 achieved the highest AUC score with a Mean AUC of 0.9997. This demonstrates the model’s exceptional ability to distinguish between different plant species.
  </div>

###   10.  What does AUC tell us about model performance?
   <div align="justify"> 
     The AUC metric measures how effectively a model can separate positive and negative classes. An AUC score of 0.9997 means there is a 99.97% probability that the model will correctly rank a positive plant instance higher than a negative one. This indicates near-perfect classification capability.
  </div>

## E. Explainability (Grad-CAM)
###   11. What did Grad-CAM reveal about model decision-making?
   <div align="justify">
     The Grad-CAM analysis revealed that the high-performing models focused on important botanical features such as the textures, shapes, and structures of plant leaves and flowers when making classifications.
  </div>

###   12.  Did the model focus on relevant image regions? 
   <div align="justify"> 
     Yes, the models focused on relevant image regions. For both ResNet50 and VGG16, the heatmaps were concentrated on the plant itself instead of the background water, indicating that the models were identifying meaningful visual features related to the target classes.
  </div>

###   13.  Which model produced the most meaningful heatmaps?
   <div align="justify">
     Among all models, ResNet50 produced the most meaningful heatmaps because its highlighted regions were more tightly focused on discriminative botanical characteristics. This observation also aligned with its high confidence levels and superior classification performance.
  </div>

## F. Model Comparison & Improvement
###   14. Which model would you recommend for deployment? Why? 
   <div align="justify">
     The model recommended for deployment is ResNet50 because it consistently achieved the highest performance across all evaluation metrics, including Accuracy, Precision, Recall, F1-score, and AUC. In addition, it outperformed the previously developed LW4 “Good Model,” making it the most reliable and robust option for real-world implementation.
  </div>

###   15.  How can you further improve your best-performing model?
   <div align="justify"> 
    The performance of the best-performing model can still be improved through fine-tuning techniques such as unfreezing selected base layers and retraining them on the dataset. Additional improvements may also come from collecting more diverse and balanced training images, especially for classes like “pickerelweed,” which showed the highest level of confusion during classification.
  </div>

## G. Real-World Application
###   16. How can your model be applied in real-world scenarios?
   <div align="justify">
     This model can be applied in different real-world scenarios such as environmental monitoring, biodiversity assessment, conservation projects, ecological research, and aquaculture management. It can help researchers and environmental agencies quickly identify aquatic plant species, detect invasive plants, and monitor the condition of lakes, rivers, and wetlands. The model can also be integrated into mobile applications so that users can identify plants by simply taking a picture.
  </div>

###   17.   What are the risks of deploying an inaccurate model? 
   <div align="justify"> 
     Deploying an inaccurate model can lead to serious problems. Incorrect predictions may cause invasive species to spread if they are not properly identified, while native species may be mistakenly removed. Inaccurate results can also lead to economic losses, poor decision-making, wasted resources, and loss of user trust in the system.
  </div>

###   18.   How can this system be integrated into a mobile/web app? 
   <div align="justify">
     This system can be integrated into a mobile or web application by converting the trained TensorFlow model into deployment-friendly formats such as TensorFlow Lite for mobile devices or TensorFlow.js for web applications. The model can either run directly on the device for real-time predictions or be hosted on a cloud server using frameworks like Flask or FastAPI. The application interface can allow users to upload images or capture photos using their device camera, then send the image to the model for classification. The app can also provide additional information about the identified plant species, prediction confidence scores, and user-friendly features to improve the overall experience.
  </div>

