# Machine-learning for image segmentation

### 🎯 Learning Objectives

* **Explain the basic principle of pixel classification for image segmentation**, including the role of image features and supervised learning.
* **Train a custom pixel classifier in ilastik** by defining pixel classes and providing representative training annotations.
* **Apply the trained classifier to segment new images** and export the resulting probability or label maps.
* **Assess the quality of the segmentation results**, identifying common errors caused by insufficient or biased training data.


--- 

Machine‑learning–based segmentation teaches a computer to recognize and delineate structures in microscopy images by example rather than by writing explicit rules for 
every possible case. 

In ***supervised learning***, you give the software a handful of images where you’ve already drawn the correct outlines (the “ground truth”).
 The program then figures out which pixel patterns—brightness, texture, edges—match your drawings. After checking that it works on a 
 few test images, it can automatically create masks on new images for you, saving hours of manual tweaking.
 
 Thus the programs learns to discern different cells or structures — much as a student might study example slides showing healthy 
 versus diseased cells to learn what visual cues distinguish them.

Here’s how it works step by step:

- **Feature Extraction** <br>
	The algorithm examines each pixel (and its local neighborhood) to compute simple characteristics—intensity, texture, edge responses, or color.

- **Model Training** <br>
	Using your labeled examples, the algorithm “learns” which combinations of features correspond to the object class (e.g., cell, nucleus, background). It builds a mathematical model—often a decision tree or a small neural network—that can predict the class of each pixel.

- **Validation** <br>
	A separate set of labeled images (the “validation” or “test” set) checks how well the model performs on new data. This helps avoid overfitting (when a model learns the training examples too exactly but fails on unseen images).

- **Prediction** <br>
	Once the model is trained and validated, you feed it new, unlabeled images. It applies the learned rules to assign each pixel to a class, producing a segmentation mask automatically.

---

### The Principle behind Pixel Classification

***Pixel classification*** is a specific type of supervised segmentation where each pixel is assigned to a category such as "signal" or "background" 
by evaluating not only its raw intensity but also a suite of engineered features (that capture local texture, edge, and spatial information.

##### Key ideas
- Each pixel is described by **image features** rather than treated in isolation.
- A classifier learns the relationship between features and classes from **annotated training data**.
- The trained model predicts class probabilities for unseen pixels.


In a typical pixel classification workflow, you:

**1. Select Features:** Choose features and scales that capture the structural and textural cues in your data.

**2. Annotate:** Scribble example regions for each class (signal vs. background).

**3. Train & Refine:** Fit a Random Forest (or similar) to your annotations, inspect the results, then iteratively add or adjust annotations until the segmentation is robust.

**4. Batch‑Apply:** Use the finalized classifier to process all images in your dataset automatically.
<br>
<br>
![Principle of Pixel Classification](pixelclassification_1.jpg)


##### Pixel classification vs. classical segmentation
- **Classical methods**: thresholding, filters, morphology, rule-based pipelines
- **Pixel classification**:
	- Handles complex textures and varying intensities
	- Reduces manual rule tuning
	- Depends strongly on training data quality



