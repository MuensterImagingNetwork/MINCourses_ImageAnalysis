# Machine-learning for image segmentation

### 🎯 Learning Objectives

* **Explain the basic principle of pixel classification for image segmentation**, including the role of image features and supervised learning.
* **Train a custom pixel classifier in ilastik** by defining pixel classes and providing representative training annotations.
* **Apply the trained classifier to segment new images** and export the resulting probability or label maps.
* **Assess the quality of the segmentation results**, identifying common errors caused by insufficient or biased training data.


--- 

## Machine Learning–Based Segmentation

Machine learning–based segmentation teaches a computer to recognize and separate structures in microscopy images **from examples rather than explicit rules**. Instead of defining fixed thresholds or handcrafted pipelines, the model learns how pixels should be classified based on annotated training data.

In **supervised learning**, users provide example annotations that label pixels as belonging to different classes (e.g. object, background). From these annotations, the algorithm learns which **image features**—such as intensity, edges, texture, and local context—are characteristic for each class. Once trained, the model can automatically segment new, unseen images.

This process is comparable to how a student learns to distinguish cell types by studying annotated reference images: patterns are learned from examples, not from written rules.

---

## The Principle of Pixel Classification

**Pixel classification** is a supervised segmentation approach in which **each pixel is assigned to a class** (e.g. signal or background) based on learned image features rather than raw intensity alone.

### Key ideas
- Each pixel is represented by a **feature vector** (intensity, edges, texture, context).
- A classifier learns the relationship between features and classes from **user annotations**.
- The trained model predicts **class probabilities** for all pixels in new images.

---

## Pixel Classification Workflow

1. **Feature extraction**  
   Image features are computed for each pixel at multiple spatial scales to capture fine detail and broader context.

2. **Annotation (training data)**  
   Users provide **sparse but representative** annotations for each pixel class.

3. **Model training and refinement**  
   A classifier (commonly a **Random Forest**) is trained on the annotated pixels. Results are inspected visually and annotations are refined iteratively until performance is stable.

4. **Application to new data**  
   The trained classifier is applied to unseen images to generate probability maps or label images, enabling batch processing of entire datasets.

![Principle of Pixel Classification](pixelclassification_1.jpg)

---

## Pixel Classification vs. Classical Segmentation

- **Classical segmentation**  
	- Thresholding, filtering, morphology, rule-based pipelines  
	→ Explicit rules defined by the user

- **Pixel classification**  
	  - Learns decision boundaries from data  
	  - Integrates multiple image cues automatically  
	  - Performs well on complex, heterogeneous images  
	  - Strongly depends on the quality and representativeness of training data



