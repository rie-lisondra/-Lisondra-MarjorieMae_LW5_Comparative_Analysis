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
    The model that achieved the highest accuracy was ResNet50 with a test accuracy of 98.57%. I think this is because ResNet50 has a deeper architecture and uses skip connections or residual blocks. These help solve the vanishing gradient problem and allow the model to learn more complex image features effectively.
  </div>

###   2.  Which model had the lowest performance? What could be the reason?
  <div align="justify">
    EfficientNetB0 had the lowest performance with only 5.65% test accuracy. This result is unusual because EfficientNetB0 is normally a strong model. A possible reason could be an issue in the implementation, preprocessing mismatch, or instability during training that prevented the model from learning properly.
  </div>

###    3. How did loss values compare across models?
   <div align="justify">
     The loss values matched the accuracy results of the models.
     <ul>
       <li>
         ResNet50 had the lowest test loss of 0.0803, which means it made the most accurate predictions.
       </li>
       <li>
         VGG16 had a test loss of 0.4347, which is higher than ResNet50 but still acceptable.
       </li>
       <li>
         EfficientNetB0 had the highest test loss of 2.9956, showing that it struggled to learn the image patterns.
       </li>
     </ul>
   </div>
  
## B. Evaluation Metrics
###  4. Why is accuracy not enough to evaluate a model?
  <div align="justify">
    Accuracy alone is not enough because it can be misleading, especially when the dataset is imbalanced. For example, if most images belong to one class, the model can get high accuracy just by predicting that class every time. Metrics like Precision, Recall, and F1-score give a clearer understanding of the model’s actual performance across all classes.
  </div>
  
###  5. Which model had the best F1-score? What does it indicate?
  <div align="justify"> 
    ResNet50 achieved the best F1-score with 0.9831. The F1-score is the balance between Precision and Recall. A high F1-score means the model can correctly identify relevant classes while also minimizing false predictions. This shows that ResNet50 is highly reliable and consistent.
  </div>

###  6. How did Precision and Recall differ across models?
  <div align="justify"> 
    <ul>
      <li>
        ResNet50 showed excellent Precision (0.9831) and Recall (0.9835), meaning it was very accurate and captured most positive instances correctly.
      </li>
      <li>
        VGG16 also performed well with Precision (0.9126) and Recall (0.9106), although slightly lower than ResNet50.
      </li>
      <li>
        EfficientNetB0 had very poor Precision (0.0026) and Recall (0.0500), which means it failed to classify most classes correctly.
      </li>
    </ul>
  </div>

## C. Confusion Matrix Analysis 

###  7. Which classes were frequently misclassified?
   <div align="justify">
     Based on the classification report:
     <ul>
       <li>
         For VGG16, classes such as cabomba, hornwort, water_clover, and water_stargrass were more frequently misclassified compared to other classes.
       </li>
       <li>
         For ResNet50, misclassifications were very minimal because most classes had very high precision and recall values.
       </li>
       <li>
         For EfficientNetB0, almost all classes were frequently misclassified, showing that the model failed to properly distinguish the plant species.
       </li>
     </ul>
  </div>
  
###  8. What patterns did you observe in the confusion matrix?
   <div align="justify">
     <p>For VGG16, there were likely some off-diagonal errors where visually similar plants were confused with each other. </p>
     <p>For ResNet50, the confusion matrix would mostly show strong diagonal values, meaning the predictions were mostly correct.</p>
     <p>For EfficientNetB0, the confusion matrix would likely show predictions concentrated in only a few classes, indicating poor generalization and strong prediction bias.</p>
  </div>
  
## D. ROC and AUC
###   9. Which model had the highest AUC score?
   <div align="justify">
     ResNet50 achieved the highest mean AUC score of 0.9993.
     <ul>
       <li>
         VGG16: 0.9953
       </li>
       <li>
         EfficientNetB0: 0.5157
       </li>
     </ul>
  </div>

###   10.  What does AUC tell us about model performance?
   <div align="justify"> 
    AUC or Area Under the Curve measures how well the model can distinguish between classes. A higher AUC means better classification performance across different thresholds. An AUC close to 1.0 indicates an excellent model, while 0.5 means the model performs almost like random guessing. Since ResNet50 had an AUC of 0.9993, it shows that the model can classify the plant species very effectively.
  </div>

## E. Explainability (Grad-CAM)
###   11. What did Grad-CAM reveal about model decision-making?
   <div align="justify">
     Grad-CAM helped visualize which parts of the image the model focused on when making predictions. It showed whether the model was looking at relevant plant features such as leaves, stems, or shapes instead of unrelated background areas.
  </div>

###   12.  Did the model focus on relevant image regions? 
   <div align="justify"> 
     <p>For high-performing models like ResNet50 and VGG16, the heatmaps were likely focused on the important parts of the plants, which means the models were using relevant visual features for classification.</p>
     <p>For EfficientNetB0, the heatmaps may have been inconsistent or focused on irrelevant regions, which reflects its poor performance.</p>
  </div>

###   13.  Which model produced the most meaningful heatmaps?
   <div align="justify">
     ResNet50 produced the most meaningful and focused heatmaps because it had the best overall performance. The highlighted regions were more aligned with the actual plant features, making its predictions easier to interpret.
  </div>

## F. Model Comparison & Improvement
###   14. Which model would you recommend for deployment? Why? 
   <div align="justify">
     I would recommend deploying ResNet50 because it consistently achieved the best results across all evaluation metrics, including accuracy, loss, F1-score, and AUC. Its performance shows that it is the most reliable and robust model for aquatic plant classification.
  </div>

###   15.  How can you further improve your best-performing model?
   <div align="justify"> 
    There are several ways to improve the ResNet50 model further:
     <ul>
       <li>Fine-tuning more layers using a lower learning rate to better adapt the model to the dataset.</li>
       <li>Applying advanced data augmentation techniques such as MixUp, CutMix, or AutoAugment.</li>
       <li>Performing hyperparameter optimization to find better learning rates, batch sizes, and dropout settings.</li>
       <li>Using ensemble methods by combining predictions from multiple strong models.</li>
       <li>Expanding the dataset with more diverse images to improve generalization.</li>
     </ul>
  </div>

## G. Real-World Application
###   16. How can your model be applied in real-world scenarios?
   <div align="justify">
     This aquatic plant classification model can be applied in different real-world scenarios such as environmental monitoring, biodiversity assessment, conservation projects, ecological research, and aquaculture management. It can help researchers and environmental agencies quickly identify aquatic plant species, detect invasive plants, and monitor the condition of lakes, rivers, and wetlands. The model can also be integrated into mobile applications so that users can identify plants by simply taking a picture.
  </div>

###   17.   What are the risks of deploying an inaccurate model? 
   <div align="justify"> 
     Deploying an inaccurate model can lead to serious problems. Incorrect predictions may cause invasive species to spread if they are not properly identified, while native species may be mistakenly removed. Inaccurate results can also lead to economic losses, poor decision-making, wasted resources, and loss of user trust in the system.
  </div>

###   18.   How can this system be integrated into a mobile/web app? 
   <div align="justify">
     This system can be integrated into a mobile or web application by converting the trained TensorFlow model into deployment-friendly formats such as TensorFlow Lite for mobile devices or TensorFlow.js for web applications. The model can either run directly on the device for real-time predictions or be hosted on a cloud server using frameworks like Flask or FastAPI. The application interface can allow users to upload images or capture photos using their device camera, then send the image to the model for classification. The app can also provide additional information about the identified plant species, prediction confidence scores, and user-friendly features to improve the overall experience.
  </div>

