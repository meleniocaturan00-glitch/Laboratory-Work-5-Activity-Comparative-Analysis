# Laboratory-Work-5-Activity-Comparative-Analysi
https://colab.research.google.com/drive/1n1UgrTDXk3-5T2IoRDyfvuwB1i-1jxiS?usp=sharing

| Model          | Train Acc | Train Loss | Val Acc | Val Loss | Precision |  Recall | F1-Score |    AUC |
| -------------- | --------: | ---------: | ------: | -------: | --------: | ------: | -------: | -----: |
| MobileNetV2    |   96.70%    | 0.1167     | **97.70%** | **0.0596** | **98.47%** | **98.05%** | **97.88%** | **0.9989**  |
| EfficientNetB0 |    96.78%    | 0.1075     | 97.30%     | 0.0663     | 98.29%     | 97.71%     | 97.49%     | 0.9977  
| InceptionV3    |    88.75%    | 0.5236     | 94.50%     | 0.1500     | 94.87%     | 94.74%     | 94.64%     | 0.9961 


| Model                | Val Accuracy | Val Loss | Precision |  Recall | F1-Score |    AUC | Notes                   |
| -------------------- | -----------: | -------: | --------: | ------: | -------: | -----: | ----------------------- |
| Teachable Machine    |       24.40% |   6.2387 |    20.80% |  24.19% |   22.00% | 0.6338 | Label order mismatch    |
| LW3 — Custom CNN     |       93.20% |   0.2215 |    94.91% |  93.18% |   92.89% | 0.9644 | Baseline improved model |
| LW4 — Enhanced CNN   |       96.70%     0.0644 |    97.80% |  96.85% |   96.68% | 0.9963 | Best custom CNN         |
| LW5 — InceptionV3    |       88.75%    | 0.5236     | 94.50%     | 0.1500     | 94.87%     | 94.74%     | 94.64%     | 0.9961   |
| LW5 — EfficientNetB0 |       96.78%    | 0.1075     | 97.30%     | 0.0663     | 98.29%     | 97.71%     | 97.49%     | 0.9977      |
| LW5 — MobileNetV2    |       96.70%    | 0.1167     | **97.70%** | **0.0596** | **98.47%** | **98.05%** | **97.88%** | **0.9989**|

 Guide Questions (Final Reflection)

A. Model Performance

1.Which pre-trained model achieved the highest accuracy? Why? MobileNetV2 achieved the highest validation accuracy at 96.19%. This model likely performed best due to its efficient architecture and effective transfer learning from ImageNet, demonstrating strong feature extraction capabilities relevant to the dataset.

2.Which model had the lowest performance? What could be the reason? InceptionV3 had the lowest performance with 85.43% validation accuracy. Its training was subject to early stopping, restoring weights from Epoch 1, suggesting that validation performance did not improve significantly, possibly due to overfitting early in training or non-optimal hyperparameters for this specific dataset.

3.How did loss values compare across models? MobileNetV2 achieved the lowest validation loss (0.0692), closely followed by EfficientNetB0 (0.0718), both indicating good model fit. InceptionV3 had the highest validation loss (0.3626), which corresponds to its lower accuracy and suggests weaker optimization or greater difficulty in learning the underlying patterns.

B. Evaluation Metrics

4.Why is accuracy not enough to evaluate a model? Accuracy can be misleading in imbalanced datasets because a model may achieve high accuracy by predicting only the majority class while failing to identify minority classes correctly. It also treats all errors equally, even when some mistakes are more critical than others. Metrics like Precision, Recall, and F1-score provide a better understanding of model performance by evaluating specific types of classification errors.

5.Which model had the best F1-score? What does it indicate? MobileNetV2 achieved the best F1-score at 95.40%, indicating the best balance between Precision and Recall among the models. This means it has a good ability to correctly identify positive instances while also minimizing false positives and false negatives.

6.How did Precision and Recall differ across models? MobileNetV2 showed the highest Precision (97.42%) and Recall (95.67%), indicating its strong capability in both correctly identifying positive instances and capturing most of them. EfficientNetB0 followed with Precision of 92.35% and Recall of 91.01%. In contrast, InceptionV3 had lower Precision (89.96%) and Recall (84.46%), meaning it produced more false positives and false negatives, leading to weaker overall performance.

C. Confusion Matrix Analysis
7.Which classes were frequently misclassified? (This analysis relies on detailed inspection of the confusion matrices which were plotted earlier. Based on the previous runs where 'converted_keras' had 0 support, it's likely classes with fewer samples or high visual similarity are still causing confusion.)

8.What patterns did you observe in the confusion matrix? (Similarly, this requires visual inspection. However, general patterns might include confusion between visually similar plant species, or certain minority classes being consistently misidentified if they were present in y_true but had low support.)

D. ROC and AUC

9.Which model had the highest AUC score? All models resulted in an AUC score of N/A (Not Applicable) or nan. This is due to warnings from sklearn indicating that ROC AUC score is not defined when only one class is present in y_true for a one-vs-rest calculation, which occurred for the 'converted_keras' class that had zero samples in the validation set.

10.What does AUC tell us about model performance? AUC (Area Under the Receiver Operating Characteristic curve) measures how well a model separates classes. In multi-class problems, it’s typically averaged across all classes (one-vs-rest). A value of 1.0 means perfect classification, while 0.5 means random guessing. However, its computation can be problematic with imbalanced or missing classes, as seen in this case.

E. Explainability (Grad-CAM)

11.What did Grad-CAM reveal about model decision-making? Grad-CAM successfully generated heatmaps for all three models (MobileNetV2, EfficientNetB0, and InceptionV3), highlighting the regions of the input image that were most influential in the models' predictions. This visualization helps to understand where each model is 'looking' when making a classification decision.

12.Did the model focus on relevant image regions? Upon visual inspection of the generated heatmaps?

MobileNetV2 (predicted: red_sage_plant, 15.91% confidence) shows concentration on areas of the plant, indicating it identified some relevant features.
EfficientNetB0 (predicted: kalmegh, 21.88% confidence) also focuses on parts of the plant, suggesting it's using visual cues from the image.
InceptionV3 (predicted: fen fang ji, 6.27% confidence) displays a more dispersed or less focused heatmap, which aligns with its lower confidence and overall performance.

13.Which model produced the most meaningful heatmaps? Based on the higher prediction confidence and more concentrated heatmaps, MobileNetV2 and EfficientNetB0 produced more meaningful heatmaps compared to InceptionV3, as they appear to highlight more specific and potentially relevant regions of the plant in the test image.

F. Model Comparison & Improvement

14.Which model would you recommend for deployment? Why? I would recommend MobileNetV2 for deployment. It achieved the highest validation accuracy (96.19%), the best F1-score (95.40%), and the lowest validation loss (0.0692). While EfficientNetB0 also performed well, MobileNetV2 demonstrated slightly superior overall performance across key metrics in this evaluation, making it the most reliable choice.

16.How can you further improve your best-performing model? Even with good results, there's always room for improvement. Further enhancements could include?

Hyperparameter Tuning: Systematically optimizing learning rate, batch size, and other model-specific parameters.
Advanced Data Augmentation: Implementing more aggressive or specialized augmentation techniques to increase data diversity.
Fine-tuning: Unfreezing some layers of the pre-trained MobileNetV2 base model and training them with a very low learning rate.
Ensemble Methods: Combining predictions from multiple top-performing models to potentially achieve higher robustness and accuracy.
Dataset Expansion: Gathering a larger and more diverse dataset to cover more variations and reduce potential biases.

G. Real-World Application

17.How can your model be applied in real-world scenarios? This herbal plant classification model, particularly the MobileNetV2 model, can have several practical applications?

User Identification: Helping individuals identify herbal plants through smartphone apps by simply uploading a photo.
Agricultural Support: Assisting farmers and cultivators in identifying plant species, monitoring growth, and potentially detecting diseases early.
Botanical Research & Conservation: Aiding botanists in cataloging species, monitoring biodiversity, and supporting conservation efforts by quickly identifying rare or endangered plants.
Education: Serving as an educational tool for students and enthusiasts to learn about different plant species.

18.What are the risks of deploying an inaccurate model? Deploying an inaccurate model carries several risks?

Misinformation: Incorrect identification could lead to users misusing plants, especially for medicinal purposes, potentially causing health risks.
Economic Loss: In agriculture, misidentification could lead to improper care, incorrect harvesting, or even loss of crops.
Environmental Impact: In conservation, incorrect identification could misdirect resources, leading to the neglect of truly endangered species or misclassification of invasive ones.
Loss of Trust: Users would quickly lose trust in an unreliable system, hindering its adoption and impact.

How can this system be integrated into a mobile/web app? To integrate the MobileNetV2 model into a mobile/web application?

Model Conversion: Convert the trained TensorFlow model to a mobile-optimized format like TensorFlow Lite for on-device inference, or deploy it as a REST API endpoint on a cloud platform (e.g., Google Cloud AI Platform) for web/server-side inference.
User Interface (UI): Develop a user-friendly interface that allows users to capture or upload images easily.
Preprocessing Pipeline: Implement the same preprocessing steps (resizing, normalization, etc.) used during training within the app to ensure consistent input to the model.
Prediction Display: Display the predicted class and its confidence score clearly to the user.
Feedback Mechanism: Consider adding a feedback mechanism where users can report misclassifications, which can be used to further improve the model over time.
Scalability: For a web app, ensure the backend infrastructure can handle concurrent requests efficiently.
